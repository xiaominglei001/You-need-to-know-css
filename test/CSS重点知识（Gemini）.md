

### **一、 CSS基础与核心概念**

这部分是理解CSS工作原理的基石。

#### **1. 语法和引入方式**

*   **基本语法**: 由一个“选择器”（Selector）和一个“声明块”（Declaration Block）组成。声明块包含一个或多个由分号分隔的“声明”（Declarations）。每个声明包含一个CSS属性名（Property）和一个值（Value），中间用冒号分隔。

    ```css
    /* 选择器  声明块       */
    /* ↓       ↓           */
    p {
      /* 属性: 值; */
      color: #333;
      font-size: 16px;
    }
    ```

*   **引入方式**:
    *   **外部样式表 (External CSS)**: 最推荐的方式，利于维护和复用。
        ```html
        <head>
          <link rel="stylesheet" href="styles.css">
        </head>
        ```
    *   **内部样式表 (Internal CSS)**: 写在HTML文件的 `<style>` 标签内，适用于单个页面的特定样式。
        ```html
        <head>
          <style>
            body {
              background-color: #f0f0f0;
            }
          </style>
        </head>
        ```
    *   **行内样式 (Inline CSS)**: 直接在HTML元素的 `style` 属性中编写，优先级最高，但通常不推荐使用，因为它混合了结构和表现。
        ```html
        <p style="color: blue; font-size: 14px;">这是一段蓝色的文字。</p>
        ```

#### **2. 选择器 (Selectors)**

选择器用于“找到”要设置样式的HTML元素。

*   **基础选择器**:
    *   **元素选择器 (Element Selector)**: `p` { ... }
    *   **类选择器 (Class Selector)**: `.my-class` { ... }
    *   **ID选择器 (ID Selector)**: `#my-id` { ... } (ID在页面中应是唯一的)
    *   **通用选择器 (Universal Selector)**: `*` { ... } (匹配所有元素，慎用)

*   **复合选择器 (Combinators)**:
    *   **后代选择器 (Descendant Selector)**: `div p` (选择 `<div>` 内的所有 `<p>` 元素)
    *   **子元素选择器 (Child Selector)**: `div > p` (只选择 `<div>` 的直接子元素 `<p>`)
    *   **相邻兄弟选择器 (Adjacent Sibling Selector)**: `h1 + p` (选择紧跟在 `<h1>` 后的同级 `<p>` 元素)
    *   **通用兄弟选择器 (General Sibling Selector)**: `h1 ~ p` (选择在 `<h1>` 之后的所有同级 `<p>` 元素)

*   **伪类 (Pseudo-classes)**: 定义元素的特殊状态。
    *   `:hover`: 鼠标悬停时。 `a:hover { color: red; }`
    *   `:focus`: 元素获得焦点时（如输入框）。 `input:focus { border-color: blue; }`
    *   `:first-child`: 作为其父元素的第一个子元素时。 `li:first-child { font-weight: bold; }`
    *   `:last-child`: 作为其父元素的最后一个子元素时。 `li:last-child { color: gray; }`
    *   `:nth-child(n)`: 选择特定位置的子元素，如 `li:nth-child(2n)` 选择所有偶数位的 `<li>`。

*   **伪元素 (Pseudo-elements)**: 为元素的特定部分设置样式。
    *   `::before`: 在元素内容 *之前* 插入生成的内容。
    *   `::after`: 在元素内容 *之后* 插入生成的内容。
        ```css
        .element::before {
          content: "► "; /* 必须有 content 属性 */
          color: green;
        }
        ```
    *   `::first-line`: 为元素的第一行文本设置样式。
    *   `::first-letter`: 为元素的第一个字母设置样式。

#### **3. 核心概念**

*   **盒模型 (Box Model)**: 每个HTML元素都可以看作一个矩形的盒子。
    *   **`content`**: 盒子的内容，显示文本和图像。
    *   **`padding`**: 内边距，内容与边框之间的空间。
    *   **`border`**: 边框。
    *   **`margin`**: 外边距，边框外的空间。
    *   **`box-sizing`**:
        *   `content-box` (默认): `width` 和 `height` 只包含 `content` 的大小。
        *   `border-box`: `width` 和 `height` 包含 `content`, `padding` 和 `border`。这是更直观的模型，推荐全局设置。
            ```css
            *, *::before, *::after {
              box-sizing: border-box;
            }
            ```

*   **层叠 (Cascade) 与继承 (Inheritance)**:
    *   **层叠**: 浏览器处理来自不同来源（浏览器默认、用户、作者）的样式规则冲突的机制。
    *   **继承**: 子元素会自动继承父元素的一些可继承属性（如 `color`, `font-family`）。

*   **优先级 (Specificity)**: 当多个规则应用到同一个元素上时，优先级高的规则生效。
    *   **优先级顺序**: 行内样式 > ID选择器 > 类选择器/属性选择器/伪类 > 元素选择器/伪元素。
    *   `!important` 拥有最高优先级，但应避免滥用。

### **二、 核心属性与文本样式**

这些是最常用的CSS属性。

*   **尺寸与间距**:
    ```css
    .element {
      width: 200px;
      height: 100px;
      padding: 15px; /* 上右下左均为15px */
      margin: 10px 20px; /* 上下10px，左右20px */
    }
    ```

*   **颜色与背景**:
    ```css
    .element {
      color: #333; /* 文本颜色 */
      background-color: #f5f5f5; /* 背景颜色 */
      background-image: url('path/to/image.jpg'); /* 背景图片 */
      background-repeat: no-repeat; /* 背景不重复 */
      background-position: center; /* 背景图片居中 */
      background-size: cover; /* 背景图片覆盖整个元素 */
    }
    ```

*   **字体与文本**:
    ```css
    .text-block {
      font-family: "Helvetica Neue", Arial, sans-serif; /* 字体族 */
      font-size: 16px; /* 字体大小 */
      font-weight: bold; /* 字体粗细: normal, bold, 100-900 */
      font-style: italic; /* 字体风格: normal, italic */
      line-height: 1.5; /* 行高，1.5倍字体大小 */
      text-align: center; /* 文本对齐: left, right, center, justify */
      text-decoration: underline; /* 文本装饰: none, underline, line-through */
      text-indent: 2em; /* 首行缩进 */
    }
    ```

### **三、 布局技术**

掌握布局是CSS的核心技能。

#### **1. 定位 (Positioning)**

*   **`position`**:
    *   `static` (默认): 遵循正常的文档流。
    *   `relative`: 相对其*原始位置*进行定位，不脱离文档流。
    *   `absolute`: 相对*最近的非static祖先元素*进行定位，完全脱离文档流。
    *   `fixed`: 相对*浏览器视口*进行定位，滚动时位置不变，常用于固定的导航栏。
    *   `sticky`: 粘性定位，在滚动到特定位置前表现为`relative`，之后表现为`fixed`。
*   **`top`, `right`, `bottom`, `left`**: 用于控制定位元素的位置。
*   **`z-index`**: 控制定位元素的堆叠顺序，数值越大越靠上（仅对定位元素生效）。

```css
.parent {
  position: relative; /* 为子元素的absolute定位创建参照 */
}

.child {
  position: absolute;
  top: 10px;
  left: 20px;
  z-index: 10;
}

.header {
  position: sticky;
  top: 0;
}
```

#### **2. 弹性盒子布局 (Flexbox)**

一维布局模型，非常适合对齐和分布项目。

*   **容器属性 (Container)**:
    *   `display: flex;` 或 `inline-flex;`
    *   `flex-direction`: 主轴方向 (`row`, `column`, `row-reverse`, `column-reverse`)。
    *   `justify-content`: 主轴对齐方式 (`flex-start`, `flex-end`, `center`, `space-between`, `space-around`)。
    *   `align-items`: 交叉轴对齐方式 (`flex-start`, `flex-end`, `center`, `stretch`, `baseline`)。
    *   `flex-wrap`: 是否换行 (`nowrap`, `wrap`, `wrap-reverse`)。
    *   `align-content`: 多根轴线的对齐方式（`flex-wrap: wrap`时生效）。

*   **项目属性 (Items)**:
    *   `flex-grow`: 放大比例（默认为0）。
    *   `flex-shrink`: 缩小比例（默认为1）。
    *   `flex-basis`: 分配多余空间前的主轴大小。
    *   `flex`: `flex-grow`, `flex-shrink`, `flex-basis` 的简写。
    *   `order`: 项目的排列顺序。
    *   `align-self`: 覆盖容器的 `align-items` 属性。

```css
.flex-container {
  display: flex;
  justify-content: space-around; /* 项目均匀分布 */
  align-items: center; /* 交叉轴居中 */
}

.flex-item {
  flex: 1; /* 每个项目等分容器宽度 */
}
```


#### **3. 网格布局 (Grid)**

强大的二维布局系统。

*   **容器属性 (Container)**:
    *   `display: grid;`
    *   `grid-template-columns`: 定义列宽。
    *   `grid-template-rows`: 定义行高。
    *   `gap` (或 `grid-gap`): 定义网格间隙。
    *   `justify-items`, `align-items`: 网格项在单元格内的对齐方式。

*   **项目属性 (Items)**:
    *   `grid-column-start`, `grid-column-end`: 定义项目跨越的列。
    *   `grid-row-start`, `grid-row-end`: 定义项目跨越的行。
    *   `grid-column`, `grid-row`: 上述属性的简写。

```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 创建三列，每列宽度平分 */
  gap: 20px;
}

.grid-item-1 {
  grid-column: 1 / 3; /* 此项目从第1条网格线跨到第3条（占两列） */
}
```

### **四、 响应式设计**

让网站适应不同尺寸的设备。

*   **视口 (Viewport)**: 在HTML的 `<head>` 中添加，是响应式设计的基础。
    ```html
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    ```

*   **媒体查询 (Media Queries)**: 根据设备特性（如视口宽度）应用不同样式。
    ```css
    /* 默认样式（移动优先） */
    .container {
      width: 100%;
    }

    /* 当屏幕宽度大于等于 768px 时（平板） */
    @media (min-width: 768px) {
      .container {
        width: 750px;
      }
    }

    /* 当屏幕宽度大于等于 1200px 时（桌面） */
    @media (min-width: 1200px) {
      .container {
        width: 1170px;
      }
    }
    ```

*   **流式布局与弹性图片**:
    ```css
    .fluid-container {
      width: 90%; /* 使用百分比宽度 */
      margin: 0 auto;
    }

    img {
      max-width: 100%; /* 防止图片超出其容器 */
      height: auto;
    }
    ```

### **五、 过渡与动画**

增加页面的动态效果，提升用户体验。

*   **过渡 (Transitions)**:
    ```css
    .button {
      background-color: #007bff;
      transition-property: background-color, transform; /* 指定过渡的属性 */
      transition-duration: 0.3s; /* 过渡时间 */
      transition-timing-function: ease-in-out; /* 过渡速度曲线 */
      transition-delay: 0s; /* 延迟时间 */

      /* 简写形式 */
      transition: all 0.3s ease-in-out;
    }

    .button:hover {
      background-color: #0056b3;
      transform: scale(1.1); /* 悬停时放大 */
    }
    ```

*   **动画 (Animations)**: 使用 `@keyframes` 创建复杂的动画序列。
    ```css
    /* 定义动画 */
    @keyframes slideIn {
      from {
        opacity: 0;
        transform: translateX(-100px);
      }
      to {
        opacity: 1;
        transform: translateX(0);
      }
    }

    /* 应用动画 */
    .animated-element {
      animation-name: slideIn; /* 动画名称 */
      animation-duration: 1s; /* 动画时长 */
      animation-timing-function: ease-out; /* 速度曲线 */
      animation-fill-mode: forwards; /* 动画结束后保持最终状态 */
    }
    ```

### **六、 高级与工程化**

提升CSS代码的可维护性和效率。

*   **CSS预处理器 (Sass/SCSS)**:
    *   **变量 (Variables)**:
        ```scss
        $primary-color: #007bff;
        a { color: $primary-color; }
        ```
    *   **嵌套 (Nesting)**:
        ```scss
        nav {
          ul { list-style: none; }
          li { display: inline-block; }
        }
        ```
    *   **混合 (Mixins)**:
        ```scss
        @mixin center-flex {
          display: flex;
          justify-content: center;
          align-items: center;
        }
        .container { @include center-flex; }
        ```

*   **CSS变量 (Custom Properties)**: 原生CSS变量，可在运行时通过JavaScript修改。
    ```css
    :root {
      --main-bg-color: #f0f0f0;
      --main-text-color: #333;
    }

    body {
      background-color: var(--main-bg-color);
      color: var(--main-text-color);
    }
    ```

*   **性能优化**:
    *   **选择器优化**: 避免使用过深、复杂的选择器。
    *   **属性优化**: 避免触发重绘(repaint)和重排(reflow)的高消耗属性，如 `top`, `left`。优先使用 `transform` 来实现位移和形变，因为它通常能利用GPU加速。
        ```css
        /* 性能较差 */
        .box {
          position: relative;
          left: 100px;
        }

        /* 性能更好 */
        .box {
          transform: translateX(100px);
        }
        ```
    *   **文件优化**: 压缩CSS文件，移除不必要的代码。

这份详细的大纲和示例涵盖了日常CSS开发中绝大部分会遇到的知识点，可以作为一份非常有用的速查手册。