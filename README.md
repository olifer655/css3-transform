一直认为感觉自己的 `css` 比较薄弱，最近无意间访问到了一个网站，感觉很好酒临摹了一下。

### 1. transform-style 实现 3D 效果

要利用 CSS3 实现 3D 的效果，最主要的就是借助 transform-style 属性。transform-style 只有两个值可以选择：

```
// 语法：
transform-style: flat|preserve-3d;

transform-style: flat; // 默认，子元素将不保留其 3D 位置
transform-style: preserve-3d; // 子元素将保留其 3D 位置。

```
当前父容器设置了 preserve-3d 值后，它的子元素就可以相对于父元素所在的平面，进行 3D 变形操作。

1、使用 translateX(length) 、translateY(length) 、 translateZ(length) 来进行 3D 位移操作，与 2D 操作一样，对元素进行位移操作，也可以合并为 translate3d(x,y,z) 这种写法；

2、使用 scaleX() 、scaleY() 、scaleY() 来进行3D 缩放操作，也可以合并为 scale3d(number,number,number) 这种写法；

3、使用 rotateX(angle) 、rotateY(angle) 、rotateZ(angle) 来进行 3D 旋转操作，也可以合并为 rotate3d(Xangle,Yangle,Zangle) 这种写法。

### 2. CSS渐变

浏览器支持两种类型的渐变：线性渐变 (linear)，通过 `linear-gradient` 函数定义，以及 径向渐变 (radial)，通过 `radial-gradient` 函数定义。

#### 2.1 线性渐变 (linear)

```
background: linear-gradient(to bottom, blue, white); // 垂直
background: linear-gradient(70deg, black, white); // 带有角度的
background: linear-gradient(to bottom, blue, white 80%, orange); // 指定位置，0%、100% 可以忽略不写
background: linear-gradient(to right, red, orange, yellow, green, blue);// 等间距色标
background: linear-gradient(to right, rgba(255,255,255,0), rgba(255,255,255,1)), url(http://foo.com/image.jpg); // 透明和渐变

```

#### 2.2 径向渐变 (radial)

```
background: radial-gradient(red, yellow, rgb(30, 144, 255));// 等间距色标
background: radial-gradient(red 5%, yellow 25%, #1E90FF 50%);// 指定间距色标
background: radial-gradient(ellipes closest-side, red, yellow 10%, #190ff 50%, white); // 椭圆的最近端
background: radial-gradient(cicle father-corner, red, yellow 10%, #190ff 50%, white);  // 圆形的最近端
```
[尺寸常量的描述](https://developer.mozilla.org/en-US/docs/Web/CSS/radial-gradient#Size_constants)

### 3. CSS动画

```
transition: 1s 1s height ease;

transition-property: height;
transition-duration: 1s;
transition-delay: 1s;
transition-timing-function: ease;

```

```
div:hover {
  animation: 1s rainbow;
}

@keyframes rainbow {
  0% { background: #c00; }
  50% { background: orange; }
  100% { background: yellowgreen; }
}
```
默认情况下，动画只播放一次。加入infinite关键字，可以让动画无限次播放。

```
div:hover {
  animation: 1s rainbow infinite;
}

```
也可以指定动画具体播放的次数，比如3次。

```
div:hover {
  animation: 1s rainbow 3;
}

```
动画结束以后，会立即从结束状态跳回到起始状态。如果想让动画保持在结束状态，需要使用animation-fill-mode属性。

```
div:hover {
  animation: 1s rainbow forwards;
}
```
animation-fill-mode还可以使用下列值:

* none：默认值，回到动画没开始时的状态。
* backwards：让动画回到第一帧的状态。
* both: 根据animation-direction（见后）轮流应用forwards和backwards规则。

动画循环播放时，每次都是从结束状态跳回到起始状态，再开始播放。animation-direction属性，可以改变这种行为。


```
div:hover {
  animation: 1s 1s rainbow linear 3 forwards normal;
}
```
```
div:hover {
  animation-name: rainbow;
  animation-duration: 1s;
  animation-timing-function: linear;
  animation-delay: 1s;
  animation-fill-mode:forwards;
  animation-direction: normal;
  animation-iteration-count: 3;
}
```
#####参考：

1. [酷炫的3D旋转透视](http://www.cnblogs.com/coco1s/p/5414153.html)

2. [CSS动画简介](http://www.ruanyifeng.com/blog/2014/02/css_transition_and_animation.html)
