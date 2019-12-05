**对于程序员来说，能过够写出易读代码是件非常了不起的事情，对于自己以后 review code 也做了很好的帮助，对于团队来说更是重中之重，团队的代码风格，能过高质量、易读更是一件了不起的事情，分享（前端）VSCode +eslint+prettier 使用 Airbnb 的代码风格配置,会以下面的标题顺序分享**

- VSCode 安装 eslint
- VSCode 安装 prettier - Code Formatter
- VSCode 配置 eslint
- VSCode 配置 prettier
- eslint 配合 prettier - Code Formatter 实现代码动态检查和 Code Formatter+eslint

## VSCode 安装 eslint

现在前端开发使用的主流编辑器 VSCode、WebStorm、ATOM、SublimeText3...,今天分享 使用 VSCode 如何产出易读、高质量的代码[VSCode 官网](https://code.visualstudio.com/)
下面安装配置

- 点击 VSCode Extendsions 按钮
- 在 search 栏中输入 eslint
- 列表中会出现 eslint 插件，点击安装
  如图，已将 eslint 安装到了 VSCode，**一些配置，一会到后面详细说明**

![eslint](https://user-gold-cdn.xitu.io/2019/12/5/16ed3ea7b948ad2a?w=970&h=1154&f=png&s=280254)

## VSCode 安装 prettier - Code Formatter

下面安装配置

- 点击 VSCode Extendsions 按钮
- 在 search 栏中输入 prettier
- 列表中会出现 prettier 插件，点击安装

如图 已将 prettier 安装到了 VSCode **一些配置，一会到后面详细说明**
![](https://user-gold-cdn.xitu.io/2019/12/5/16ed3f9ad1f49f68?w=984&h=1044&f=png&s=225498)

## VSCode 配置 eslint

可以看到 eslint 的配置参数，如图
![eslint配置说明](https://user-gold-cdn.xitu.io/2019/12/5/16ed4021986e3e83?w=1876&h=1516&f=png&s=351785)
打开 VSCode Preferebces -> Setings,如图
![VSCode 配置选择](https://user-gold-cdn.xitu.io/2019/12/5/16ed400f17c580ba?w=1064&h=950&f=png&s=766105)
接着就是配置 eslint 的配置参数，有两种配置方式
1 、 一种是通过带有 ui 的方式配置，如图

![](https://user-gold-cdn.xitu.io/2019/12/5/16ed40651dbbb140?w=1540&h=1378&f=png&s=183971)
2、 通过 settings.json 配置方式 workbench.settings.editor 选择为 json，（可以全局设置、用户设置 我选择用户设置）[settings.json](https://github.com/zhangfaliang/VSCodeEslintPrettierAndEslint/blob/master/settings.json)

![](https://user-gold-cdn.xitu.io/2019/12/5/16ed409b11c7dff9?w=1352&h=870&f=png&s=164711)

上面的选择可以根据自己爱好来选择，配置设置如下

```
//保存时自动修复打开或关闭保存时自动修复。
"eslint.autoFixOnSave": true,
// #每次保存的时候自动格式化
"editor.formatOnSave": true,
//控制是否为JavaScript文件启用eslint
"eslint.enable": true,
//验证应由ESLint验证的语言ID数组
"eslint.validate": [
    {
        "language": "typescript",
        "autoFix": true
    },
    {
        "language": "typescriptreact",
        "autoFix": true
    }
],
```

现在我们打开一个 js 或者 ts 文件进行编辑保存 ctr+s，进行保存的时候就会根据 eslint 的配置进行格式化，如图

![](https://user-gold-cdn.xitu.io/2019/12/5/16ed4539cacff1cf?w=920&h=540&f=gif&s=2826837)

## VSCode 配置 prettier - Code Formatter

可以看到 prettier 的配置参数，如图

![](https://user-gold-cdn.xitu.io/2019/12/5/16ed4354d9eedb7c?w=1880&h=1432&f=png&s=266837)

1、 通过 settings，方式 workbench.settings.editor 选择为 json，（可以全局设置、用户设置 我选择的用户）

![](https://user-gold-cdn.xitu.io/2019/12/5/16ed454de85b3822?w=1568&h=1060&f=png&s=260855)

```
//settings.json 中设置
  "editor.defaultFormatter": "esbenp.prettier-vscode"
```

2 、右击文件，选择 格式化的时候，会出现些问题，如图

![](https://user-gold-cdn.xitu.io/2019/12/5/16ed4623def39d03?w=752&h=518&f=gif&s=2079279)

## eslint 配合 prettier - Code Formatter 实现代码动态检查和 Code Formatter 继承 eslint

在项目的根目录下执行

```
yarn add eslint --dev
yarn add prettier --dev
yarn add --dev eslint-config-prettier eslint-plugin-prettier
// yarn eslint --init 直接会创建一个 .eslintrc.js 这里的rules 可以配置自定义规范
yarn eslint --init

// 在 .eslintrc.js 的extends属性中添加"plugin:prettier/recommended":
{
  "extends": ["plugin:prettier/recommended",....]
}
```

搞定了，可以学规范的代码了，ctr+s 的时候就会帮你纠正不太规范的代码了
This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).
