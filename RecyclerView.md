# 滚动控件

## ListView
- 用于展示大量数据
- 只能实现纵向滚动
- 借助适配器来传递数据给ListView（通过泛型指定要适配的数据类型）
- 点击事件：setOnItemClickListener()
- 运行效率比较低：Adapter中的getView()方法每次都会重新加载布局，且会调用View的findViewById()获取实例；分别借助convertView 和 ViewHolder优化


## RecyclerView
- 优化版ListView
- 需在build.gradle添加RecyclerView库的依赖
- 创建新的 xxAdapter类，继承至RecyclerView.Adapter<RecyclerView.ViewHolder>
```
 重写方法：
 onCreateViewHolder()
 onBindViewHolder()
 getItemCount()
```
- 在主类使用RecyclerView：
```
val layoutManager = LinearLayoutManager(this)
layoutManager.orientation = LinearLayoutManager.HORIZONTAL 
// 瀑布流: val layoutManager = StaggeredGridLayoutManager(3, StaggeredGridLayoutManager.VERTICAL)
// 网格： GridLayoutManager
recyclerView.layoutManager = layoutManager
val adapter = xxAdapter(data) // data to show
recyclerView.adapter = adapter
```
- 点击事件：需自己给子项具体的View注册点击事件--> 在onCreateViewHolder()中实现（不同于ListView）

## Epoxy.RecyclerView
