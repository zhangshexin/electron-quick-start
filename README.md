# electron-quick-start

**Clone and run for a quick way to see Electron in action.**

This is a minimal Electron application based on the [Quick Start Guide](https://electronjs.org/docs/tutorial/quick-start) within the Electron documentation.

**Use this app along with the [Electron API Demos](https://electronjs.org/#get-started) app for API code examples to help you get started.**

A basic Electron application needs just these files:

- `package.json` - Points to the app's main file and lists its details and dependencies.
- `main.js` - Starts the app and creates a browser window to render HTML. This is the app's **main process**.
- `index.html` - A web page to render. This is the app's **renderer process**.

You can learn more about each of these components within the [Quick Start Guide](https://electronjs.org/docs/tutorial/quick-start).

## To Use

To clone and run this repository you'll need [Git](https://git-scm.com) and [Node.js](https://nodejs.org/en/download/) (which comes with [npm](http://npmjs.com)) installed on your computer. From your command line:

```bash
# Clone this repository
git clone https://github.com/electron/electron-quick-start
# Go into the repository
cd electron-quick-start
# Install dependencies
npm install
# Run the app
npm start
```

Note: If you're using Linux Bash for Windows, [see this guide](https://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/) or use `node` from the command prompt.

## Resources for Learning Electron

- [electronjs.org/docs](https://electronjs.org/docs) - all of Electron's documentation
- [electronjs.org/community#boilerplates](https://electronjs.org/community#boilerplates) - sample starter apps created by the community
- [electron/electron-quick-start](https://github.com/electron/electron-quick-start) - a very basic starter Electron app
- [electron/simple-samples](https://github.com/electron/simple-samples) - small applications with ideas for taking them further
- [electron/electron-api-demos](https://github.com/electron/electron-api-demos) - an Electron app that teaches you how to use Electron
- [hokein/electron-sample-apps](https://github.com/hokein/electron-sample-apps) - small demo apps for the various Electron APIs

## License

[CC0 1.0 (Public Domain)](LICENSE.md)




electron按装过程 


一、镜象

prefix=D:\Develop\nodejs\node_global
cache=D:\Develop\nodejs\node_cache
registry=https://registry.npm.taobao.org/
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
phantomjs_cdnurl=http://npm.taobao.org/mirrors/phantomjs
ELECTRON_MIRROR=http://npm.taobao.org/mirrors/electron/
electron_custom_dir=6.1.7

说明：
1、第1，2行是自定义的npm install xxx -g的位置和缓存位置

2、第3-6行是镜象
3、第7行是在electron-packager执行是从淘宝镜象下载是返回404找不到文件问题的解决方法，使用固定的customDir


二、在按装electron过程中

1、一直出现not promised，下不了按装不了的问题 ，在win7中试了只有7.0.0之前的才可以或者去镜象地址下载下来使用npm install electron-prebuild但这样按装的版本很低不推荐

三、打包过程 

1、 Make sure that .NET Framework 4.5 or later and Powershell 3 or later are installed, otherwise extracting the Electron zip file will hang.

四、electron-packager和electron-builder

1、electron-packager只能打包不能生成安装包，electron-builder支持的更多，包更小
2、eletron-builder/electron-packager配置
----------------------------------
在package.json中做如下配置

"build": {
    "appId": "com.xxx.app",
    "mac": {
      "target": ["dmg","zip"]
    },
    "win": {
      "target": ["nsis","zip"]
    }
},
"scripts": {
    "dist": "electron-builder --win --x64"
},
---------------------------------
electron-packager配置

package.json中的scripts中
"pack": "electron-packager . quzhengzhuanjia --win --out ../myClient --arch=x64 --app-version=0.0.1 --electron-version=6.1.7",

对electron-builder详细讲解的链接：https://segmentfault.com/a/1190000016695922?utm_source=tag-newest
在下载依赖时总失败的处理方式【需翻墙】：https://blog.csdn.net/cctvcqupt/article/details/87904368

五、devDependencies与dependencies的区别
dependencies 表示我们要在生产环境下使用该依赖，devDependencies 则表示我们仅在开发环境使用该依赖。在打包时，一定要分清哪些包属于生产依赖，哪些属于开发依赖，尤其是在项目较大，依赖包较多的情况下。若在生产环境下错应或者少引依赖包，即便是成功打包，但在使用应用程序期间也会报错，导致打包好的程序无法正常运行。



