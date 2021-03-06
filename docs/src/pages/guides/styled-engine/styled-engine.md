# Styled engine

<p class="description">Configure your preferred styling engine.</p>

The default engine used for generating styles for Material-UI components is [emotion](https://github.com/emotion-js/emotion).
All the components of Material-UI rely on the `styled()` API to inject CSS into the page.
This API is supported by multiple popular styling engines.
It makes it possible to support multiple ones.

## How to switch to styled-component?

If you already have [styled-components](https://github.com/styled-components/styled-components) installed, it's possible to use it exclusively by skipping emotion.
There are currently two packages available:

- `@material-ui/styled-engine` - a thin wrapper around emotion's `styled()` API, with the addition of few other required utilities, such as the `<GlobalStyles />` component, the `css` and `keyframe` helpers, etc.
- `@material-ui/styled-engine-sc` - a similar wrapper around `styled-components`.

These two packages implement the same interface. It makes it possible to replace one with the other.
By default, `@material-ui/core` has `@material-ui/styled-engine` as a dependency, but you can configure your bundler to replace it with `@material-ui/styled-engine-sc`.
For example, if you are using webpack you can configure this by adding a resolver:

**webpack.config.js**

```js
module.exports = {
  //...
  resolve: {
    alias: {
      '@material-ui/styled-engine': '@material-ui/styled-engine-sc',
    },
  },
};
```

If you are using create-react-app, there is a ready-to-use template in the example projects.
You can use the [create-react-app-with-styled-components example](https://github.com/mui-org/material-ui/tree/next/examples/create-react-app-with-styled-components), or its [TypeScript version](https://github.com/mui-org/material-ui/tree/next/examples/create-react-app-with-styled-components-typescript).

> **Note** that `@emotion/react`, `@emotion/styled`, and `styled-components` are optional peer dependencies of `@material-ui/core`, so you need to install them yourself. See the [Installation guide](/getting-started/installation/) for more info.

> **Note** that this package swap approach is identical to the replacement of [Preact](https://github.com/preactjs/preact) with React. The Preact's team has documented a large number of installation configurations. If you are stuck with Material-UI + styled-components, don't hesitate to check out how they solve the problem, you can likely transfer the solution.
