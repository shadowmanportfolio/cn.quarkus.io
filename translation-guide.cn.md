# quarkus.io 翻译项目翻译指南

quarkus.io 翻译项目正在翻译 [quarkus.io] (https://quarkus.io)。

##翻译方法

[quarkus.io] (https://quarkus.io) 是一个使用 Jekyll 的静态站点，其内容由 asciidoctor (.adoc) 描述。
该存储库位于 [quarkusio / quarkusio.github.io] (https://github.com/quarkusio/quarkusio.github.io)，并在 CC BY 3.0 下发布。
在这个项目中，我们使用名为 po4a 的实用程序从 .adoc 文件中提取文本，对其进行翻译，将其写回 .adoc 文件，然后构建它以构建一个日文版网站。
使用 po4a 提取文本、使用翻译记忆库应用翻译文本、通过机器翻译草稿翻译和回写处理的工作流程由该存储库的 GitHub Actions 自动化。
提取的文本作为 .po 文件保存在 [l10n 目录] (l10n) 下，这是一种管理翻译文本的文件格式。

## 对翻译的贡献

如果您愿意为翻译做出贡献，请在本地克隆此存储库，编辑 [l10n 目录] (l10n) 下的 .po 文件，并发送拉取请求。
您可以从 [此处] (l10n / stats / translation.csv) 检查每个文件的翻译状态。

## 声明开始翻译

在开始翻译工作时，为了避免多个成员同时处理同一个文件和重复工作造成的浪费。
请在 GitHub 问题上声明您要开始处理的文件和范围。
相反，当您提出问题时，请确保有人已经在现有问题中声明了对目标的工作。

###翻译工作

.po 文件是一个文本文件，但各种翻译辅助工具都支持编辑。例如，[POEdit] (https://poedit.net/)
支持Windows/Mac/Linux执行，快捷键丰富，编辑时使用方便。

### 翻译目标的自动导入和翻译

当 [quarkus.io] (https://quarkus.io) 更新时，要翻译的文件将通过 GitHub Actions 的工作流程定期添加到此存储库中。
它将自动导入并创建一个 .po 文件。.po 文件包含存储在翻译记忆库中的现有翻译，并且
使用 [quarkus-adoc-po-translator] (https://github.com/doc-l10n-kit/quarkus-adoc-po-translator)
将插入 DeepL API 自动翻译的翻译文本，因此请在翻译时将其用作粗略翻译。

但是，由于是机器翻译到最后，所以有很多不自然的部分，例如teniwoha，并且标记为“需要确认”（模糊），除非“需要确认”标记，否则不会反映为翻译被删除...
请检查并更正翻译并删除“需要确认”标记。

### 翻译文件

以后想翻译[l10n目录](l10n)下的所有.po文件，但首先主要内容是“指南”。
用[l10n/po/ja_JP/_guides目录]翻译“博客”(l10n/po/ja_JP/_guides)
[l10n/po/ja_JP/_posts 目录] (l10n/po/ja_JP/_posts) 我想以目录为中心进行翻译。

###无翻译句子的处理

.po 文件可能包含不需要完整翻译的句子，例如源代码和 URL。
在这种情况下，无需照原样复制原始文本。请把翻译留空。然后将按原样使用原始文本。

### 翻译结果预览

如果你翻译 .po 文件并得到一个 pull-request，站点将自动使用 GitHub Actions 构建，你可以临时浏览站点的 URL 将是
它将在大约 5 分钟后作为评论发送到 GitHub 上的 Pull-Request。
您可以从该临时站点查看翻译结果的预览，因此请使用它。

### HTML 模板更新支持/翻译

quarkus.io 的内容是用 asciidoctor (.adoc) 编写的，但 Jekyll 的 HTML 模板中包含一些文本。
Jekyll的HTML模板写的文本不能在po4a中编程，所以放到[l10n/override目录]（l10n/override）。
放置 po4a 无法处理的文件的副本，手动翻译此文件，并在构建 Jekyll 站点时使用这些文件。
本地化是通过覆盖原始文件来实现的。
如果在上游端更新了原始文件，也需要更新复制到[l10n/覆盖目录]（l10n/覆盖）端的文件端。
请注意，此时上游侧没有检测和通知更新原始文件的功能。
