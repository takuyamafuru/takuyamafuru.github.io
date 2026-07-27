# タクヤマ的 Quartz 站点

这是一个面向中文学术写作的 Quartz 5 站点骨架。`content/` 可以直接作为 Obsidian Vault 打开，也可以继续用 VS Code 编辑。

## 本地预览

环境要求：

- Node.js 22 或更高版本
- npm 10.9.2 或更高版本

首次使用：

```powershell
npm ci
npx quartz plugin install --from-config
npx quartz build --serve
```

浏览器访问 `http://localhost:8080`。

## 写作与发布

所有公开页面都必须在 YAML frontmatter 中包含：

```yaml
publish: true
```

未显式标记的 Markdown 不会生成到网站。`content/private/`、`content/templates/` 和 `content/.obsidian/` 也会被忽略。

建议直接在 Obsidian 中打开 `content/` 文件夹。文章模板位于：

- `content/templates/article-template.md`
- `content/templates/paper-reading-template.md`

## GitHub Pages

推荐创建名为 `takuyamafuru.github.io` 的空仓库，这样网站默认地址就是：

```text
https://takuyamafuru.github.io
```

创建仓库后，在本项目目录中添加远程地址：

```powershell
git remote add origin https://github.com/takuyamafuru/takuyamafuru.github.io.git
git push -u origin v5
```

随后在 GitHub 仓库的 **Settings → Pages → Source** 中选择 **GitHub Actions**。项目内已经包含部署工作流。

如果最终使用其他仓库名，例如 `garden`，需要把 `quartz.config.yaml` 中的 `baseUrl` 改成：

```yaml
baseUrl: takuyamafuru.github.io/garden
```

绑定自定义域名时，也只需修改这一项并在 GitHub Pages 中配置相同域名。
