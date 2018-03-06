# css3-object-fit-img-
使用css新标准属性实现图片的自适应

### 在响应式设计(RWD)中，令大家最头痛的问题的是图片的自适应处理问题。往往我采取的处理方式是给图片的容器设置一个尺寸，然后给图片设置下面的代码：
<pre>
img {
    max-width: 100%;
    height: auto;
}
</pre>
但往往需要处理的只止于此。你可能想要让图像长宽比例来填充他的整个容器，和想重新定位他的中心位置。或者，如果你想按长宽比例响应式调整iframe，你可能会真正的碰到麻烦。当然也有修复的方法，但所有人都在说：

媒体调整的行为将会失控！

是的，现在我们将要解决这个问题。CSS标准提出属性object-fit和object-position可以解决这样的问题。

Chris Mills在2011年发表了一篇The CSS3 object-fit and object-position properties，文章中详细介绍了object-fit和object-position属性的使用。今天我们也将深入学习和了解这两个属性的具体使用。

功能简介

在CSS中，替换元素(replaced elements)，如<img>和<video>元素一直存在长宽比的控制问题，特别在在响应式设计中，如何在不同设备，不同分辨率下对这些元素的长宽进行响应。例如，您可能想不以图片的正确尺寸，不想扭曲图像，也不想失去图像的长宽比例，让图片占据一定的空间。按照长宽比例调整和缩略图像的画面比挤压和拉伸图像是一个更优雅的解决方案。

在CSS3中我们可以使用object-fit和object-position来处理。“object-fit”属性指定了替换元素的内容应该如何使用他的宽度和高度来填充其容器。“object-position”属性指定了替换元素在容器中的对齐方式。

语法和取值说明

欲要了解这两个属性的具体使用，我们先从其语法和属性值作用入手。

object-fit语法

object-fit属性的语法非常的简单：

object-fit:fill | contain | cover | none | scale-down
object-fit取值说明

object-fit主要适合于替换元素，比如：<video>、<object>、<img>、<input type="image">、<svg>、<svg:image>和<svg:video>等。其默认值为fill。object-fill取值的说明如下：

 fill:此值为boject-fit的默认值，替换内容的大小被设置为填充元素的内容框，也就是说，元素的内容扩大到完全填充容器的外形尺寸，即使这打破其内在的宽高比。
 contain：替换元素内容大小保持长宽比例填充元素内容容器，其具体对象大小被解析为一个包含元素的宽度和高度。也就是说，如果你在替换元素上设置一个明确的高度和宽度，此值将导致内容大小，完全在固定的比例显示，但仍在元素尺寸内显示。
 cover：替换元素内容大小保持长宽比例填充元素内容容器，其具体对象大小被解析为覆盖整个元素的宽度和高度。也就是说，替换元素内容大小保持长宽比，但改变宽度和高度，以便完全覆盖内容元素。
 none：替换元素内容不调整大小以适应内部元素的容器，内容完全忽略设置在元素上的任何高度和权重，并且仍在元素尺寸内显示。
 scale-down：当内容大小设置了non或contain，将导致具体对象变得更小。

 
浏览器兼容性

object-fit和object-position属性到目前为止，浏览器的兼容并不很好，支持的浏览器仅有Opera12.1(还需要添加其私有前缀-o-)和Opera Mobile11.5~12.1。不过值得庆幸的是Chrome32+将会支持这两个属性。其详细的兼容说明如下所示：

在写本教程的时候，你可以使用Google Chrome Canary浏览器来进行测试。（在下文中的用例，使用的是Google Chrome Canary33进行的效果测试）。