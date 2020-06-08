---
title: 关于 Nuxt.js
description: "Nuxt是一个基于Vue.js的渐进式框架，用于创建现代Web应用程序。它基于Vue.js官方库（vue，vue-router和vuex）和强大的开发工具（webpack，Babel和PostCSS）"
---

> Nuxt是一个基于Vue.js的渐进框架，用于创建现代Web应用程序。它基于Vue.js官方库（vve，vue-router和vuex）和强大的开发工具（webpack，Babel和PostCSS）Nuxt的目标是使Web开发功能强大且性能卓越。

## Nuxt.js 是什么？

Nuxt是一个框架，旨在按照官方Vue指南为您提供强大的体系结构。

它可逐步采用，可用于创建从静态登录页面到复杂的企业就绪Web应用程序。

本质上是多功能的，它支持不同的目标(server, serverless or static)，并且服务器端呈现是可切换的。

可通过强大的模块生态系统进行扩展，从而轻松连接REST或GraphQL端点，常用的CMS，css框架等，PWA和AMP支持只是Nuxt项目的一个模块。

NuxtJs是您的Vue.js项目的中坚力量，它提供了构建框架的结构，使您可以放心而又灵活。

## Nuxt.js 框架是如何运作的？

![基于 Vue、Webpack 和 Babel](https://i.imgur.com/avEUftE.png)

Nuxt.js 集成了以下组件/框架，用于开发完整而强大的 Web 应用：
- [Vue 2](https://github.com/vuejs/vue)
- [Vue-Router](https://github.com/vuejs/vue-router)
- [Vuex](https://github.com/vuejs/vuex) (当配置了 [Vuex 状态树配置项](/guide/vuex-store) 时才会引入)
- [Vue 服务器端渲染](https://ssr.vuejs.org/en/) (排除使用 [`mode: 'spa'`](/api/configuration-mode))
- [Vue-Meta](https://github.com/nuxt/vue-meta)

压缩并 gzip 后，总代码大小为：**57kb** （如果使用了 Vuex 特性的话为 60kb）。

另外，Nuxt.js 使用 [Webpack](https://github.com/webpack/webpack) 和 [vue-loader](https://github.com/vuejs/vue-loader) 、 [babel-loader](https://github.com/babel/babel-loader) 来处理代码的自动化构建工作（如打包、代码分层、压缩等等）。

## 特性

- 基于 Vue.js(`*.vue`)
- 自动代码分层
- 服务端渲染
- 强大的路由功能，支持异步数据
- 静态文件服务
- ES2015+ 语法支持
- 打包和压缩 JS 和 CSS
- HTML 头部标签管理
- 本地开发支持热加载
- 集成 ESLint
- 支持各种样式预处理器： SASS、LESS、 Stylus 等等
- 支持 HTTP/2 推送
- 扩展模块化架构

## 流程图

下图阐述了 Nuxt.js 应用一个完整的服务器请求到渲染（或用户通过 `<nuxt-link>` 切换路由渲染页面）的流程：

![nuxt-schema](/nuxt-schema.svg)

## 服务端渲染(通过SSR)

您可以使用**Nuxt.js**作为框架来处理项目的所有UI呈现。

启动时`nuxt`，它将启动具有热更新加载的开发服务器，并且[Vue 服务器端渲染](https://ssr.vuejs.org/en/)配置为自动为服务器呈现应用程序。

### 单页应用程序 (SPA)

如果您不想使用服务器端渲染或需要应用程序提供静态托管，则可以使用 `nuxt --spa` 命令即可使用 `SPA` 模式。
它为您提供了强大的SPA部署机制，无需使用 `Node.js` 来运行应用程序或任何特殊的服务器端处理。

可以查看 Nuxt.js 提供的各种 [命令](/guide/commands) 来了解更多相关使用信息。

如果你的项目有自己的 Web 服务器（例如用 Express.js 启动的Web服务），你仍然可以将 Nuxt.js 当作是中间件来使用，负责UI渲染部分的功能。在开发通用的 Web 应用过程中，Nuxt.js 是可插拔的，没有太多的限制，可通过 [开发编码中使用Nuxt.js](/api/nuxt) 了解更多的信息。

## 静态化 (预渲染)

支持 Vue.js 应用的静态化算是 Nuxt.js 的一个创新点，通过 `nuxt generate` 命令实现。

该命令依据应用的路由配置将每一个路由静态化成为对应的 HTML 文件。

<div>
  <a href="https://vueschool.io/courses/static-site-generation-with-nuxtjs?friend=nuxt" target="_blank" class="Promote">
    <img src="/static-site-generation-with-nuxtjs.png" alt="Static Site Generation with Nuxt.js by vueschool"/>
    <div class="Promote__Content">
      <h4 class="Promote__Content__Title">使用Nuxt.js生成静态站点</h4>
      <p class="Promote__Content__Description">了解如何生成静态站点(预渲染)用来提高性能和搜索引擎优化(SEO)，同时减少站点托管成本。</p>
      <p class="Promote__Content__Signature">由VueSchool制作视频课程，用于支持Nuxt.js开发</p>
    </div>
  </a>
</div>

例如，以下文件结构：

```bash
-| pages/
----| about.vue
----| index.vue
```

静态化后变成：
```
-| dist/
----| about/
------| index.html
----| index.html
```

静态化可以让你在任何一个静态站点服务商托管你的Web应用。

Nuxt.js 的官网就是一个绝佳的例子, 它静态化后托管在 [Netlify](https://www.netlify.com) 上，也可以参考我们的 [源代码](https://github.com/nuxt/nuxtjs.org) 。

我们不希望每次更新部署 [@nuxt/docs 仓库](https://github.com/nuxt/docs) 的时候都要手工执行 `nuxt generate` 命令生成静态文件，它会触发 Netlify 的钩子应用：

1. 克隆 [nuxtjs.org repository](https://github.com/nuxt/nuxtjs.org)
2. 使用 `npm install` 命令安装依赖
3. 运行 `npm run generate`
4. 生成 `dist` 目录

我们现在就有了一个 **无服务端的自动静态化的Web应用** :)

我们进一步考虑下电商应用的场景，利用 `nuxt generate`，是不是可以将应用静态化后部署在 CDN 服务器，每当一个商品的库存发生变化时，就重新静态化下，更新下商品的库存。但是如果用户访问的时候恰巧更新了呢？我们可以通过调用电商的 API ，保证用户访问的是最新的数据。这样相对于传统的电商应用来说，这种静态化的方案可以大大节省服务器的资源。

<div class="Alert">

查看 [如何在Netlify上部署？](/faq/netlify-deployment) 来获取更多相关信息。

</div>
