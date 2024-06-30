# 关于Mdtht

**Mdtht**（Markdown to Html Theme）是使用 Javascript和 CSS 为 Markdown编辑器开发的一款插件。目的是在将 .md 文件导出为html文件或预览时，自动生成侧边目录、文档样式。

可以在任何支持添加 js 和 css 的Markdown编辑器中使用，如：**Typora**、**MarkdownPad** ......

# 实现的功能

**Mdtht**提供了如下功能：

1. 高亮和暗黑两种文档风格模式（根据系统自动切换，也可手动设置）
2. 根据 html 文档中 h1~h6 标签的位置自动生成对应层级的目录和序号
3. 自动生成侧边栏目录导航
4. 标题序号显示或隐藏
5. 目录层级树状图
6. 三种目录图标样式
7. 文字阴影效果
8. 一键展开收起子目录
9. 一键展开收起侧边栏
10. 根据阅读区内容自动追踪所在目录
11. 目录搜索
12. 代码高亮插件 highlightjs 样式美化，[highlightjs网址](https://highlightjs.org/)
13. 根据个人喜好个性化配置样式

# 最终效果

**亮色模式**

![整体效果](./img/mdtht-1.png)

**暗色模式**

![夜览模式](./img/mdtht-2.png)

**目录收起效果**

![目录收起效果](./img/mdtht-5.png)

**3 种目录样式及隐藏目录编号**

![3 种目录样式](./img/mdtht-3.jpg)

**搜索功能效果**

![搜索功能效果](./img/mdtht-4.png)

# 如何使用

## 在Typora中使用

在**Typora**中使用步骤如下：

1. 打开 `偏好设置` -> `导出` -> `点击右侧的 + 按钮` -> `从模版添加，选择HTML(without Styles)` -> `添加` -> `修改刚才添加的模版名称，如：Mdtht`
2. 点击添加的模版 Mdtht -> `在<head/>文本框中`  -> `输入：<style> </style>` -> 粘贴 **mdtht.min.css** 的代码到`<style>`标签对中，如：`<style> 复制 mdtht.min.css 的代码到这里 </style>`
3. `在<body/>文本框中`  -> `输入：<script> </script>` -> 粘贴 **mdtht.min.js** 的代码到`<script>`标签对中，如：`<script> 复制 mdtht.min.js 的代码到这里 </script>`
4. 样式文件添加完成。
5. 代码高亮：
    1. 下载 highlight.min.js，[highlight.min.js复制下载地址](https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js "highlight.min.js")
    2. 参照第 3 步将 highlight.js 代码复制到 `<body/>文本框中`
    3. **在 highlight.min.js 代码的最后位置添加代码： `hljs.highlightAll();` 完成**。
6. 导出 html 时选择刚刚添加的 Mdtht 模版即可。


## 在MarkdownPad中使用

在**MarkdownPad**中使用步骤如下：

1. 复制 dist 文件夹中的 **mdtht.min.css** 的代码。

2. 打开 MarkdownPad -> `工具`  -> `选项`  -> `样式表` -> `添加`

3. 然后粘贴 **mdtht.min.css** 的代码 -> 给样式表取一个以.css结尾的名字 -> `保存并关闭`

4. 复制 dist 文件夹中的 **mdtht.min.js** 的代码。

5. 打开 MarkdownPad -> `工具`  -> `选项`  -> `高级` -> `Html Head编辑器`  -> 在代码编辑器中输入 `<script> </script>` 标签对，然后粘贴 **mdtht.min.js** 的代码到标签对中： `<script> 复制mdtht.min.js的代码放到这里 </script>`  -> `保存并关闭`

6. 代码高亮：
    1. 下载 highlight.min.js，[highlight.min.js复制下载地址](https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js "highlight.min.js")
    2. 参照第 5 步将 highlight.js 代码复制到 `新的<script>标签对中`
    3. **在 highlight.min.js 代码的最后位置添加代码： `hljs.highlightAll();` 完成**。

7. 保存并关闭，完成。

# 如何自定义初始化配置

### 初始化参数说明

| 参数顺序 | 参数            |  类型   | 默认值 | 说明                                                         |
| :------: | :-------------- | :-----: | :----: | :----------------------------------------------------------- |
|    1     | indexStyle      | Number  |   1    | 目录样式，**该值只有：1，2，3** 三个选项，默认样式 1         |
|    2     | firstTagToTitle | Boolean | fasle  | 是否将第一个标题作为文档标题，不计入目录中，默认关闭         |
|    3     | titleCenter     | Boolean |  true  | 文章标题是否居中，**该选项只有 firstTagToTitle 为 true 时才有效** |
|    4     | showIndex       | Boolean | false  | 是否显示目录编号，默认显示目录编号                           |
|    5     | showTitleIndex  | Boolean | false  | 是否开启正文标题序号，默认关闭                               |
|    6     | showTree        | Boolean |  true  | 是否开启目录层级树状线，默认开启                             |
|    7     | openShadow      | Boolean | false  | 是否开启文字阴影，默认关闭                                   |
|    8     | openDark        | Boolean | fasle  | 是否开启为黑夜模式，false 为白天模式，true 为黑夜模式，**该选项优先级低于系统模式，但仍可手动切换** |

### 自定义初始化设置

如果你想根据个人喜好初始化相关样式，请按照下面的步骤：

1. 在 **mdtht.min.js** 文件中的最后位置找到 `new Mdtht`
2. 根据自身需求按上面的参数说明**依次按顺序配置**
3. 将修改后的文件保存

自定义配置示例：

**在mdtht.min.js文件中配置示例:**

1. 打开 mdtht.min.js

2. 在代码最后处找到: `new Mdtht`

3. 开始配置，如配置为**目录样式2，将第一个标题作为文档标题，文章标题居中，则配置为：** `new Mdtht(2,true,true)`

4. 保存退出

配置参数顺序示例：

`new Mdtht(indexStyle,firstTagToTitle,titleCenter,showIndex,showTitleIndex,showTree,openShadow,openDark);`

> [!ImPORTANT]
>
> **注意：**如果要配置第 N 个参数，则第 N 个之前的参数也要依次配置，如要配置第3个参数则第1、第2个参数也要配置。

---

🐳 如果您喜欢该文档样式风格，还请给一个 star 😄，使用过程中有什么问题请及时提交 issues。