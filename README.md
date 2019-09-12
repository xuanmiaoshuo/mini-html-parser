# mini-html-parser2

forked from [ant-mini-program/mini-html-parser](https://github.com/ant-mini-program/mini-html-parser)，为了兼容Taro，将所有依赖包都打进一个文件，避免Taro.build时找不到require的文件

## 安装

```
$ npm install @jiahuix/mini-html-parser2 --save
```

## 使用

```js
// page.js
const html = `<div>
<span>test</span>
<div>
    <span>table test</span>
    <table>
        <thead>
            <tr>
                <th>title</th>
                <th>title</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td colspan="2">yy</td>
                <td>xx</td>
                <td>xx</td>
                <td>xx</td>
            </tr>
        </tbody>
    </table>
</div>
</div>`
import parse from 'mini-html-parser2';

Page({
  data: {
    nodes: [],
  },
  onLoad() {
    parse(html, (err, nodes) => {
      if (!err) {
        this.setData({
          nodes,
        });
      }
    })
  },
})
```

```html
<!-- page.axml -->
<rich-text nodes="{{nodes}}" />
```

## 运行测试

```
$ npm run build
$ npm test
```
