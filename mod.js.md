- //模块的导出
- //在到处模块文件中只能有一个默认导出（default）；当需要导出一个变量时不需要加const，var，let
- export default function a(){
    console.log(1111)
}

- export let c = 100
- export const d = 200
- export var b = 333

- //模块的导入; 导入时，变量需要用花括号包起来
- // 第一种导入方式：可按导出名原样导入；
- // 第二中导入方式：一次性导入所有，然后定义一个名称代词，通过这个名称代词去调用导出的变量、函数或者类；
- // 第三种导入方式：当导出模块中有默认导出时，导入时可以自定义导入名称，其他按原导出名称导入； 

- //1
- import a, {b,c,d} from "./mod.js"

- //2
- import * as newmod from './mod.js'

- //3
- import A,{b,c,d} from './mod.js'

- //新语法转译成兼容性旧语法
    - //目录结构
    - //父目录
    - //trans
        - //子目录
        - //lib  这个目录时转译后的代码文件
        - //src  这个目录中放新语法写的代码文件
- //转译时，切到trans目录下
- npm init
- //设置国内源地址，在当前目录创建一个".npmrc"文件。内容为
- registry=https://registry.npm.taobao.org
- //然后执行
- npm install babel-core babel-cli --save-dev 
- //修改package.json文件，增加如下：
- "script": {
    "build": "babel src -d lib"
}

- //创建一个".babelrc"文件，内容如下：
-  {
    "presets": ["env"]
}

- //安装依赖
- npm install babel-preset-env --save-dev 

- //当用新语法开发完代码后，在项目根目录下执行;这是语法就转译完成，
- npm run build 