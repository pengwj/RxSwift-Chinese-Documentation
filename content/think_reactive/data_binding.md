## 数据绑定

![](/assets/FunctionalReactiveProgramming/Binding.png)

在**函数响应式编程**里有一个比较重要的概念就是**数据绑定**。就是指将**可被监听的序列**绑定到**观察者**上：

我们对比一下这两段代码：

```swift
let image: UIImage = UIImage(named: ...)
imageView.image = image
```

```swift
let image: Observable<UIImage> = Observable.from(...)
image.bind(to: imageView.rx.image)
```

第一段代码是我们非常熟悉的，它就是将一个单独的图片设置到`imageView`上。

第二段代码则是将一个图片序列同步到`imageView`上。这个序列里面的图片可以是异步产生的。这里定义的 `image` 就是上图中蓝色部分（**可被监听的序列**），`imageView.rx.image`就是上图中橙色部分（**观察者**）。而这种同步机制就是**数据绑定**。