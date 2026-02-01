# D013 中医古籍知识图谱问答系统vue+django+neo4j python实现《五十二病方》

> 完整项目收费，可联系QQ: 81040295 微信: mmdsj186011 注明从git来的，谢谢！
也可以关注我的B站： 麦麦大数据 https://space.bilibili.com/1583208775
> 

up主B站：  **麦麦大数据**
关注B站，有好处！

编号:  D013
## 视频

[video(video-5dbciySq-1758356339353)(type-bilibili)(url-https://player.bilibili.com/player.html?aid=833149127)(image-https://i-blog.csdnimg.cn/img_convert/b0db36ae60bfd29de5f6a8bc56c3e991.jpeg)(title-vue+django 中医传统典籍可视化与问答系统《五十二病方》)]
## 1 系统简介
系统简介：本系统是一个基于Vue + Django + MySQL + Neo4j构建的中医古籍知识图谱与问答系统，聚焦于马王堆汉墓帛书《五十二病方》的内容挖掘与智能交互。系统主要包括：知识图谱可视化模块，用于展示古籍中病症、中药、古中医名词等实体及其关系；模糊检索功能，支持用户快速查询相关古籍内容；智能问答模块，允许用户咨询古方的病症、中药用法或古中医名词释义，并提供自动的现代文翻译拓展；用户管理模块，涵盖登录、注册、退出登录功能，以及个人设置（支持修改个人信息、头像和密码），确保用户数据的安全性和个性化体验。
## 2 功能设计
该系统采用B/S（浏览器/服务器）架构模式。用户通过浏览器访问Vue前端界面，该前端由HTML、CSS、JavaScript以及Vue.js生态系统中的Vuex（用于状态管理）、Vue Router（用于路由导航）和Echarts/D3.js（用于知识图谱可视化）等组件构建。前端通过API请求与Django后端进行数据交互，Django后端负责业务逻辑处理，并利用ORM工具与MySQL数据库（存储用户信息、系统配置等结构化数据）和Neo4j图数据库（存储知识图谱实体和关系数据）进行数据持久化。此外，系统还包含一个独立的爬虫或数据导入模块，用于从原始古籍资料中提取数据并构建知识图谱，为整个系统提供数据支撑。智能问答功能基于知识图谱和自然语言处理技术实现，支持用户查询的语义理解和结果返回。
### 2.1系统架构图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/1fe20bbc09fd4eaaacb2ee904bd5055d.png)
### 2.2 功能模块图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/316c94a1c5dd40bd804eafa549ed0afd.png)
## 3 功能展示
### 3.1 登录 & 注册
登录界面背景是一个视频，展示和本文系统主题相匹配的内容，登录和注册界面在一个界面下，通过按钮来切换，注册界面输入用户名和密码，会检查这个用户是否存在，登录界面则要检查用户名是否存在以及用户名密码是否正确：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2deac9bbe9654bdc999bc9d23be318a2.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/264ea768a9cf4fabaa00351838b78a41.png)
### 3.2 主页
如果通过校验，则可以进入主页，在主页是一个左侧菜单，右侧操作面板的布局，右上角是登录用户的头像和退出按钮：
### 3.3 知识图谱
知识图谱可视化，使用echarts实现
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4906594b00ea448ead130662ffddef81.png)
支持对知识图谱的模糊查询，从而查找子图：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/31403299dc664bb9804ff00c2b4314a5.png)
知识图谱所使用的数据：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/1cdc6e00e7ff4b6f8561cd2d69ca8b9a.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/da07fb9625c143f597d4293dc69b303c.png)

neo4j界面下图谱内容：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/fa0d20a511df447a8c9f9bb95c619539.png)
### 3.4 问答系统
可以咨询中医古老医书的相关内容：

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/9dcdd505656f42599f06604d2a174e92.png)

### 3.5 个人设置
个人设置方面包含了**用户信息修改**、**密码修改**功能。
用户信息修改中可以上传头像，完成用户的头像个性化设置，也可以修改用户其他信息。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/fa676c07768440a0a95bcf123de7efc4.png)
修改密码需要输入用户旧密码和新密码，验证旧密码成功后，就可以完成密码修改。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4578d88a1d004c60b311a23fe6d7cccf.png)
## 4程序代码
### 4.1 代码说明
代码介绍：这是一个基于Vue.js的《五十二病房》中医古籍可视化实现。代码创建了一个古典风格的网页界面，展示了古籍的目录和内容。主要功能包括：1. 古籍目录的展示和点击交互；2. 鼠标点击切换章节内容；3. 古典风格的文字排版和布局。代码使用了Vue.js的数据绑定和事件处理功能，实现了目录与内容的动态切换。样式采用了传统中医古籍的设计风格，包括仿宋字体、木质背景和古色古香的配色方案。
### 4.2 流程图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d239e5c887b54df89ebff541ce2789d6.png)

### 4.3 代码实例
```python
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>五十二病房古籍可视化</title>
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=SimSun&display=swap" rel="stylesheet">
    <style>
        /* 古籍风格CSS */
        body {
            font-family: 'SimSun', serif;
            background: #f5e6d3;
            margin: 0;
            padding: 20px;
        }
        .book-container {
            max-width: 1200px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .chapter-title {
            color: #2c3e50;
            font-size: 24px;
            text-align: center;
            margin-bottom: 20px;
        }
        .content {
            line-height: 1.8;
            text-indent: 2em;
        }
        .catalog {
            padding: 20px;
            background: #f8f9fa;
            border-radius: 5px;
            margin-bottom: 20px;
        }
        .catalog h2 {
            color: #2c3e50;
            margin-bottom: 15px;
        }
        .catalog li {
            margin-bottom: 8px;
        }
        .catalog a {
            color: #2c3e50;
            text-decoration: none;
            cursor: pointer;
        }
        .catalog a:hover {
            color: #e67e22;
        }
    </style>
</head>
<body>
    <div id="app" class="book-container">
        <div class="catalog">
            <h2>目录</h2>
            <ul>
                <li v-for="(chapter, index) in chapters" :key="index">
                    <a @click="showChapter(index)">{{ chapter.title }}</a>
                </li>
            </ul>
        </div>
        <div class="chapter-content">
            <h1 class="chapter-title">{{ currentChapter.title }}</h1>
            <div class="content" v-html="currentChapter.content"></div>
        </div>
    </div>

    <script>
        const { createApp } = Vue;

        const chapters = [
            {
                title: "风疟",
                content: `
                    <p>风疟者，往来寒热，脉痹肢节，故名风疟。</p>
                    <h3>症状</h3>
                    <p>发作时寒战，继以发热，热退再寒，往来寒热。</p>
                    <h3>诊断</h3>
                    <p>诊其脉，虚实知因，热多于寒，实也；寒多于热，虚也。</p>
                    <h3>治疗</h3>
                    <p>以青蒿素、黄芩等药物为主，清热解暑。</p>
                `
            },
            // 添加更多章节
        ];

        createApp({
            data() {
                return {
                    chapters,
                    currentChapter: chapters[0]
                }
            },
            methods: {
                showChapter(index) {
                    this.currentChapter = this.chapters[index];
                }
            }
        }).mount('#app');
    </script>
</body>
</html>
```
-----
## 联系方式：
