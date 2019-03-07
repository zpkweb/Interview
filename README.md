# Interview
f2e Interview

切记：不要一问一答，善于沟通。不要被动的回答问题，可以将知识延伸，聊到自己擅长的领地
自己的职业规划：认真想想，已3-5年为界	
想想最后问面试官的问题				
		
					css面试	

一、css盒模型
	css中的盒子模型包括IE盒子模型和标准的W3C盒子模型。
border-sizing: border-box, inherit, content-box
标准盒子模型： 左右border+左右padding+contentwidth
IE盒子模型border-box: width = content+padding+border 元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制
inherit: 从父类继承box-sizing的值

二、前端一像素问题（画一条0.5px的线）
* transform: scaleY（0.5） 使用伪元素设置1px的边框，然后对边框进行缩放(s
caleY)
　实现思路：
     1、设定目标元素的参考位置
     2、给目标元素添加一个伪元素before或者after，并设置绝对定位
     3、给伪元素添加1px的边框
     4、用box-sizing: border-box 属性把边框都包进宽和高里面
     5、宽和高设置为 200%
     6、整个盒子模型缩小为0.5
     7、调整盒子模型的位置，以左上角为基准 transform-origin: 0 0;
* border-image 设置图片的边框

三、4.transition和animation的区别
	Animation和transition大部分属性是相同的，他们都是随时间改变元素的属性值，他们的主要区别是transition需要触发一个事件才能改变属性，
	而animation不需要触发任何事件的情况下才会随时间改变属性值，并且transition为2帧，从from .... to，而animation可以一帧一帧的。
	
	transition 规定动画的名字  规定完成过渡效果需要多少秒或毫秒  规定速度效果  定义过渡效果何时开始
	animation  指定要绑定到选择器的关键帧的名称
	

四、不定宽高的DIV居中	
	1.使用flex  在父盒子设置display: flex; justify-content: center;align-items: center
	2.使用css的transform  	父盒子设置:display:relative
				Div 设置: transform: translate(-50%，-50%);position: absolute;top: 50%;left: 50%;
	3.display：table-cell   父盒子设置:display:table-cell; text-align:center;vertical-align:middle;
				Div 设置: display:inline-block;vertical-align:middle;
		
五、浮动 https://juejin.im/post/5a954add6fb9a06348538c0d
	特性：浮动元素影响的不仅是自己，他会影响周围元素对其进行环绕
      为什么要清除浮动？（解决父元素高度坍陷问题）
	一个块级元素如果没有设置height,其height由子元素撑开，对子元素使用了浮动之后，子元素就会脱离文档流
	也就是说，父及元素中没有内容可以撑开其高度，这样父级元素height就会被忽略。这就是所谓的高度坍塌
      如何清除浮动
	1.给父级元素定义高度 2.让父级元素也浮动 3.父级定义display:table 4.父元素设置overflow:hidden 
	clearfix:使用内容生成的方式清除浮动
		.clearfix:after {  // :after选择器向选定的元素之后插入内容
   			content:""; // 生成内容为空
   			display: block; // 块级元素显示
   			clear:both; // 清除前面元素
			}
	不破坏文档流，没有副作用

七、position
	值：relative,static（默认值）,absolute,sticky,fixed
	absolute会根据上一级position的值不为static进行定位，如果向上一直没有找到position，则相对整个body进行定位
	fixe相对的是视图的窗口，或者frame框架（setFram的子框架，一种html标签）

八、css选择器分类：
	   基本的：
		1.id选择器（id="name"）
		2.类选择器（class="head"）
		3.标签选择器（body, div, ul, li）
		4.全局选择器（*）
	   复杂的：
		1.组合选择器（.head .head_logo）
		2.后代选择器 （#head .nav ul li 从父集到子孙集）
		3.群组选择器 (div, span, img {color:Red} 具有相同样式的标签分组显示)
		4.继承选择器
		5.伪类选择器（链接样式，a元素的伪类）
		6.子选择器（div>p, 带大于号>）
		7.CSS相邻相邻兄弟选择器（h1+p, 带加号+）

九、CSS优先级
	不同级别：总结排序：!important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性
		1.属性后面加!import 会覆盖页面内任何位置定义的元素样式
		2.作为style属性写在元素内的样式
		3.id选择器
		4.类选择器
		5.标签选择器
		6.通配符选择器（*）
		7.浏览器自定义或继承
	同一级别：后写的会覆盖先写的

 css选择器的解析原则：选择器定位DOM元素是从右往左的方向，这样可以尽早的过滤掉一些不必要的样式规则和元素
	
十、对于行内元素，font-size指定 他们的content area的高度，由于inline box = 上下的helf-leading，如果leading为0，在这种情况下，font-size指定了inline box的高度
		font-size 指的是字体的高度，但是不能指定每个字形给定字体高度下的实际高度，导致了span的高度大于line-height

十一、z-index属性  z-index 属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。
			position的值的属性大于z-index   Z-index 仅能在定位元素上奏效（例如 position:absolute;）
			元素可拥有负的 z-index 属性值

十二、块元素和行内元素
	1.块元素会独占一行，默认情况下，其宽度自动填满父元素宽度 行元素不会占据一行，会一直排在一行，直到一行排不下
	2.行元素没有宽度和高度属性，块级元素即使设置了宽度，还是会独占一行
	块级元素： div  p forn ul li h1-h6
	行内元素：span img input a i

十三、如何画一个三角形：  设置宽高，然后用border去画
  			   width: 0;
        		   height: 0;
        		   border-bottom: 100px solid cyan;
        		   border-left: 50px solid transparent;
        		   border-right: 50px solid transparent;

十四、伪类：link 表示链接正常情况下（即页面加载完成时）显示的颜色
	    hover:表示鼠标悬停时显示的颜色
	    visited:链接被点击时显示的位置
	    focus：元素获得光标焦点时的颜色
	    active: 元素处于激活状态
	link -> visited -> hover -> focus -> active

十五、雪碧图：多个图片集成在一个图片中的图
		使用雪碧图可以减少网络请求的次数，加快允许的速度
		通过background-position，去定位图片在屏幕的哪个位置

十六、使元素消失的方法
	visibility:hidden、display:none、z-index=-1、opacity：0
	1.opacity：0,该元素隐藏起来了，但不会改变页面布局，并且，如果该元素已经绑定了一些事件，如click事件也能触发
	2.visibility:hidden,该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已经绑定的事件
	3.display:node, 把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素删掉
	

							布局面试
一、flex弹性布局， 
	可以简单的使一个元素居中（包括水平和垂直居中）
栅格式系统布局，bootstrap grid

二、圣杯和双飞翼布局 三栏是布局（两边两栏宽度固定，中间栏宽度自适应）
	方案一：position（绝对定位法） center的div需要放在最后面
		绝对定位法原理将左右两边使用absolute定位，因为绝对定位使其脱离文档流，后面的center会自然流动到他们的上卖弄，然后margin属性，留出左右两边的宽度。就可以自适应了。
	方案二：float 自身浮动法 center的div需要放到后面
		自身浮动法的原理就是对左右使用float:left和float：right，float使左右两个元素脱离文档流，中间的正常文档流中，使用margin指定左右外边距对其进行一个定位。
	圣杯布局：原理就是margin负值法。使用圣杯布局首先需要在center元素外部包含一个div,包含的div需要设置float属性使其形成一个BFC，并且这个宽度和margin的负值进行匹配

三、左边定宽，右边自适应
	方案一：左边设置浮动，右边宽度设置100%  .left{float:left}  .right:{width:100%}
	方案二：左设置浮动，右用cacl去补宽度计算 .left{float:left} .right:{width:cacl(100vw-200px}
	方案三：父容器设置display：flex  right部分是设置flex：1
	方案四：右边div套个包裹、并前置、左及包裹 双浮动

四、水平居中
	行内元素居中（父元素text-align:center）
	块状元素居中（块状元素没发用text-align）
		1.宽度一定：margin:auto
		2.宽度不定：块级变行内，然后在父上text-aligin
			    float

四、BFC https://juejin.im/post/5909db2fda2f60005d2093db
	理解：BFC是css布局的一个概念，是一块独立的渲染区域，一个环境，里面的元素不会影响到外部的元素
	如何生成BFC：（脱离文档流）
		     【1】根元素，即HTML元素（最大的一个BFC）
		     【2】float的值不为none
		     【3】position的值为absolute或fixed
		     【4】overflow的值不为visible（默认值。内容不会被修剪，会呈现在元素框之外）
		     【5】display的值为inline-block、table-cell、table-caption
	BFC布局规则：1.内部的Box会在垂直方向，一个接一个地放置。
		     2.属于同一个BFC的两个相邻的Box的margin会发生重叠
		     3.BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此, 文字环绕效果，设置float
		     4.BFC的区域不会与float box重叠。
		     5.计算BFC的高度，浮动元素也参与计算
	BFC作用：1.自适应两栏布局
		 2.可以阻止元素被浮动元素覆盖
		 3.可以包含浮动元素---清除内部浮动 原理:：触发父div的BFC属性，使下面的子div都处在父div的同一个BFC区域之内
		 4.分属于不同的BFC时，可以阻止margin重叠
	
							js面试
一、 this的指向
	1.当函数作为对象的方法被调用时，this就会指向该对象。
	2.作为普通函数，this指向window。
	3.构造器调用，this指向返回的这个对象。
	4.this的隐式丢失
	5.箭头函数  箭头函数的this绑定看的是this所在函数定义在哪个对象下，就绑定哪个对象
      		    如果有嵌套的情况，则this绑定到最近的一层对象上

		this指向的固定化，并不是因为箭头函数内部有绑定this的
		机制，实际原因是箭头函数根本没有自己的this，导致内部的this就是外
		层代码块的this。正是因为它没有this，所以也就不能用作构造函数。

	怎么改变this的指向呢？ 1.使用es6的箭头函数；2.在函数内部使用that = this；3.使用apply，call，bind； 4.new实例化一个对象

二、什么是闭包和原型链
	内部函数可以访问定义他们外部函数的参数和变量。（作用域链的向上查找，把外围的作用域中的变量值存储在内存中而不是在函数调用完毕后销毁）设计私有的方法和变量，避免全局变量的污染
	函数嵌套函数
	本质是将函数内部和外部连接起来。优点是可以读取函数内部的变量，让这些变量的值始终保存在内存中，不会在函数被调用之后自动清除
   闭包的缺陷：
		1.闭包的缺点就是常驻内存会增大内存使用量，并且使用不当容易造成内存泄漏
		2.如果不是因为某些特殊任务而需要闭包，在没有必要的情况下，在其它函数中创建函数是不明智的，因为闭包对脚本性能具有负面影响，包括处理速度和内存消耗。   


   内存溢出和内存泄漏（给的不够用| 用了不归还）
	内存溢出：在程序中申请内存时，没有足够的内存空间供其使用，出现out of memory；比如申请了一个integer,但给它存了long才能存下的数，那就是内存溢出
	内存泄漏：在程序申请内存后，无法释放已申请的内存空间，一次内存泄漏危害可以忽略，但内存泄漏堆积后果很严重，无论多少内存，迟到会被占光

   举列子：闭包中的this,对象函数。匿名函数返回函数return function
 
   作用域：(由当前环境与上层环境一系列的变量对象组成！！！保证 当先执行环境里，有权访问的变量和函数是有序的，作用域链变量只能被向上访问)
	定义：由当前环境与上层环境的一系列变量对象组成(函数嵌套函数，内部一级级往上有序访问变量或对象)
	作用是：保证当前执行环境里，有权访问的变量和函数时有序的，作用域链的变量只能被向上访问
		变量访问到window对象及被终止，作用域链向下访问是不允许的
		1.改变作用域有 with try..中的catch，
		2.所有为定义的直接赋值的变量自动声明为全局作用域

	作用域：一套规则，管理引擎如何在当前作用域以及嵌套的子作用域中根据标识符名称
		查找变量（标识符就是变量或者函数名）（只用全局作用域和局部作用域）（作用域在它创建的时候就存在了）

	代码执行分为两个阶段：
		1.代码编译阶段：有编译器完成，将代码翻译可执行的代码，这个阶段会被确定
		2.代码执行阶段：有js引擎完成，主要执行可执行的大妈，这个阶段执行上下文被创建（对象被创建）
	
	执行上下文：一个看不见得对象，存在若干个属性和变量，它被调用的时候创建的。函数被调用查看的this指向的object，object就是上下文（只有被调用的时候创建）

   作用域链: https://blog.csdn.net/yooungt13/article/details/20581635
	    · 当代码在一个环境中执行时，会创建变量对象的一个作用域链,
		举例子：var name ="Tom"
			function sayHi () {
			    alert('Hi,'+name)
			}
			sayHi()  //Hi, Tom
		函数sayHi()的执行环境为全局环境，所以它的变量对象为window。当函数执行到name时，先查找局部环境，找到则换回，否则顺着作用域查找，在全局环境中，
		找到name返回，这一查找变量的有序过程的依据就是作用域。
	
	    · 作用域链是保证执行环境有权访问的所有变量和函数的有序访问

   原型链：函数的原型链对象constructor默认指向函数本身，原型对象除了有原型属性外，为了实现继承，还有一个原型链指针_proto_,
	   该指针是指向上一层的原型对象，而上一层的原型对象的结构依然类似。因此可以利用_proto_一直指向Object的原型对象上，而Object
	   原型对象用Object.prototype._proto_  = null表示原型链顶端。如此形成了js的原型链继承。同时所有的js对象都有Object的基本防范
	
三、类的创建和继承
	（es5）new 一个function，在这个function的prototype里增加属性和方法, 类里面有方法和属性
	 (es6)中class, extends
	1. 继承：
 		原型链继承： function Cat(){ } Cat.prototype = new Animal(); Cat.prototype.name = 'cat'; 无法实现多继承
		构造继承：使用父类的构造函数来增强子类实例。function Cat(name){Animal.call(this);this.name = name || 'Tom';} 无法继承父类原型链上的属性跟方法  installof去检验
		实例继承：为父类实例添加新特性，作为子类实例的返回
		拷贝继承：拷贝父类元素上的属性跟方法
		组合继承：构造继承 + 原型继承的组合体
		寄生组合继承：通过寄生方式，在构造继承上加一个Super函数(没有实例和方法) 让他的原型链指向父类的原型链 
			      砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性
	2. 如何判断是那种类型？ 

	3.给两个构造函数A和B，如何实现A继承B （Object.prototype）
		function A(....){} A.prototype...
		function B(....){} B.prototype...
		A.prototype = Object.create(B.prototype)  再A的构造函数里new B(props)		
	
	   使用new一个函数的话，函数里的构造函数的参数就为undefined，里面的一些函数可能执行错误，因为this改变了	
		Object.create =  function (o) {
   			var F = function () {};
   			F.prototype = o;
   			return new F();
			};

		
四、异步回调（如何解决回调地狱）
	promise、generator、async/await
	
	promise： 1.是一个对象，用来传递异步操作的信息。代表着某个未来才会知道结果的时间，并未这个事件提供统一的api，供进异步处理
		  2.有了这个对象，就可以让异步操作以同步的操作的流程来表达出来，避免层层嵌套的回调地狱
		  3.promise代表一个异步状态，有三个状态pending（进行中），Resolve(以完成），Reject（失败）
		  4.一旦状态改变，就不会在变。任何时候都可以得到结果。从进行中变为以完成或者失败
			promise.all() 里面状态都改变，那就会输出，得到一个数组
			promise.race() 里面只有一个状态变为rejected或者fulfilled即输出
			promis.finally()不管指定不管Promise对象最后状态如何，都会执行的操作（本质上还是then方法的特例）
 
五、前端事件流
	事件流描述的是从页面中接受事件的顺序，事件 捕获阶段 处于目标阶段 事件冒泡阶段 addeventListener 最后这个布尔值参数如果是true，表示在捕获阶段调用事件处理程序；如果是false，表示在冒泡阶段调用事件处理程序。
	  1、事件捕获阶段：实际目标div在捕获阶段不会接受事件，也就是在捕获阶段，事件从document到<html>再到<body>就停止了。
          2、处于目标阶段：事件在div发生并处理，但是事件处理会被看成是冒泡阶段的一部分。
          3、冒泡阶段：事件又传播回文档
       阻止冒泡事件event.stopPropagation()
 		  function stopBubble(e) {
        		if (e && e.stopPropagation) { // 如果提供了事件对象event 这说明不是IE浏览器
          		e.stopPropagation()
        		} else {
          		window.event.cancelBubble = true //IE方式阻止冒泡
        	      }
      		   }
       阻止默认行为event.preventDefault()
	 function stopDefault(e) {
        if (e && e.preventDefault) {
          e.preventDefault()
        } else {
          // IE浏览器阻止函数器默认动作的行为
          window.event.returnValue = false
        }
      }
事件如何先捕获后冒泡？
  在DOM标准事件模型中，是先捕获后冒泡。但是如果要实现先冒泡后捕获的效果，
	对于同一个事件，监听捕获和冒泡，分别对应相应的处理函数，监听到捕获事件，先暂缓执行，直到冒泡事件被捕获后再执行捕获事件。
	
哪些事件不支持冒泡事件：鼠标事件：mouserleave  mouseenter
			焦点事件：blur focus
			UI事件：scroll resize


六、事件委托（提高性能）
	简介：事件委托指的是，不在事件的（直接dom）上设置监听函数，而是在其父元素上设置监听函数。通过事件冒泡，父元素可以监听到子元素上事件的触发
	      通过判断事件发生元素DOM的类型，来做出不同的响应。
	举例子： 最经典的就是ui和li标签的事件监听，比如我们在添加事件的时候，采用事件委托机制，不会在li标签上直接添加，而是在ul父元素上添加
	好处：可以比较合适动态元素的绑定，新添加的子元素也会监听函数，也可以有事件触发机制
	

七、js的new操作符做了什么？
	new操作符创建了一个空对象，这个对象原型指向构造函数的prototype，执行构造函数后返回这个对象（return this）。
	如果不要父类的属性跟方法，在函数的prototype上去new这个父类。

八、改变函数内部this指针的指向函数(bind,apply,call)
	通过apply和call改变函数的this指向，他们两个函数的第一个参数都是一样的表示要改变指向的那个对象，第二个参数，apply是数组，而call则是arg1,arg2...这种形式。



	bind 一个是返回一个函数，并不会立即执行 第二个是带参数（第一个参数要指向的this，后面的的参数用来传递

九、深拷贝和浅拷贝 https://juejin.im/post/5b00e85af265da0b7d0ba63f 从堆和栈都是内存中划分出来用来存储的区域开始讲起
	基本类型：undefined,null,Boolean,String,Number,Symbol 在内存中占据固定大小，保存在栈内存中
	引用类型：Object,Array,Date,Function,RegExp等	引用类型的值是对象 保存在堆内存中，栈内存存储的是对象的变量标识符以及对象在堆内存中的存储地址。
	 基本类型的复制: 其实就是创建了一个新的副本给将这个值赋值给新变量， 改变值旧对象不会改变
	 引用类型的复制： 其实就是复制了指针，这个最终都将指向同一个对象，改变其值新对象也会改变
	基本类型的比较 == 会进行类型转换

	浅拷贝：仅仅就是复制了引用，彼此操作不影响，slice() concat()  object.assign
	深拷贝：在堆中重新分配内存，不同的地址，相同的值,互不影响的 JSON.parse()将一个js对象序列化为一个json字符串  JSON.stringify()将json字符串反序列化为一个js对象  es6的展开 {...}
	深拷贝和浅拷贝的主要区别是：在内存中的存储类型不同
		浅拷贝：重新在堆栈中创建内存，拷贝前后对象的基本类型互不影响。只拷贝一层，不能对对象进行子对象进行拷贝
		深拷贝：对对象中的子对象进行递归拷贝，拷贝前后两个对象互不影响
	
十、跨域
	同源策略（协议+端口号+域名要相同）
	1、jsonp跨域(只能解决get）
		原理：动态创建一个script标签。利用script标签的src属性不受同源策略限制，因为所有的src属性和href属性都不受同源策略的限制，可以请求第三方服务器资源内容
		步骤：1.去创建一个script标签
		      2.script的src属性设置接口地址
		      3.接口参数，必须要带一个自定义函数名，要不然后台无法返回数据
		      4.通过定义函数名去接受返回的数据    	
		
	2、document.domain 基础域名相同 子域名不同
    	3、window.name 利用在一个浏览器窗口内，载入所有的域名都是共享一个window.name
    	4、服务器设置对CORS的支持
		原理：服务器设置Access-Control-Allow-Origin HTTP响应头之后，浏览器将会允许跨域请求
   	5、利用h5新特性window.postMessage()

	iframe元素创建包含另外一个文档的内联框架（行内框架）(setTimeout进行异步加载)
      解释：浏览器中的浏览器！用于设置文本或者图形的浮动图文框或容器
      它和跨域
        1、document.domain 实现主域名相同，子域名不同的网页通信
          都设置为超域：document.domain = 'demo.com'
        2、window.postMessageht(data, url)，h5的API，启动跨域通信


十一、图片的懒加载和预加载
	预加载：提前加载图片，当用户需要查看是可以直接从本地缓存中渲染
	  为什么要使用预加载：在网页加载之前，对一些主要内容进行加载，以提供用户更好的体验，减少等待时间。
			      否则，如果一个页面的内容过于庞大，会出现留白。
		解决页面留白的方案：1.预加载  2.使用svg站位图片，将一些结构快速搭建起来，等待请求的数据来了之后，替换当前的占位符
	实现预加载的方法：
	 		1.使用html标签
			2.使用Image对象
			3.使用XMLHTTPRequest对像，但会精细控制预加载过程



	懒加载（lazyload）：客户端优化，减少请求数和延迟请求数
		提升用户体验，
		减少无效资源的加载
		防止并发加载的资源过多会阻塞js的加载，影响网站的正常使用
	  原理：首先将页面上的图片的src属性设置为空字符串，而图片的真是路经则设置带data-original属性中，
		当页面滚动的时候需要去监听scroll事件，在scroll事件的回调中，判断我们的懒加载的图片是否进入到可视区域
		，如果图片在可视区域将图片的src属性设置为data-original的值，这样就可以实现延迟加载。	

十二、函数节流防抖
	什么是防抖：短时间内多次触发同一个事件，只执行最后一次，或者在开始时执行，中间不执行。比如公交车上车，要等待最后一个乘客上车
        什么是节流：节流是连续触发事件的过程中以一定时间间隔执行函数。节流会稀释你的执行频率，比如每间隔1秒钟，只会执行一次函数，无论这1秒钟内触发了多少次事件
	都为解决高频事件而来， scroll mousewhell mousemover touchmove onresize

十三、将arguments类数组转化为数组的方法
	Array.apply(null, arguments)
	Array.prototype.slice.apply(arguments)
	Array.from(arguments)

十四、高阶函数
	一、函数作为参数传递 抽离出一部分容易变化的业务逻辑，把这部分业务逻辑放在函数参数中。这样一来可以分离业务代码中变化与不变的部分
		回调函数
	二、函数作为返回值传递

十五、如何判断一个变量是对象还是数组（prototype.toString.call()）。
	千万不要使用typeof来判断对象和数组，因为这种类型都会返回object。
	typeOf()是判断基本类型的Boolean,Number，symbol, undefined, String。
		对于引用类型：除function，都返回object   null返回object。
	installOf() 用来判断A是否是B的实例，installof检查的是原型。
	toString() 是Object的原型方法，对于 Object 对象，直接调用 toString()  就能返回 [Object Object] 。而对于其他对象，则需要通过 call / apply 来调用才能返回正确的类型信息。
	
	hasOwnProperty()方法返回一个布尔值，指示对象自身属性中是否具有指定的属性，该方法会忽略掉那些从原型链上继承到的属性。
	
	isProperty()方法测试一个对象是否存在另一个对象的原型链上。

	
十六、setTimeout 和 setInterval的机制
	因为js是单线程的。浏览器遇到etTimeout 和 setInterval会先执行完当前的代码块，在此之前会把定时器推入浏览器的
	待执行时间队列里面，等到浏览器执行完当前代码之后会看下事件队列里有没有任务，有的话才执行定时器里的代码
							
十七、var let const
	const：定义的变量不可修改，必须初始化 ，
	var：定义的变量可以修改，如果不初始化输出undefined，不会报错
	let：块级作用域，函数内部使用let定义后，会函数外部无影响
	let const 不会造成变量的提升

十八、js垃圾回收机制
	1.JS具有自动垃圾收集的机制
	2.JS的内存生命周期（变量的生命）
		1.分配你所需要的空间 var a = 20
		2.使用分配带的内存（读写） alert（a + 10）
		3.不适用的时候，释放内存空间 a = null 
	3.JS的垃圾收集器每隔固定的时间就执行一次释放操作，通用的是通过标记清除的算法
	4.在局部作用域中，垃圾回收器很容易做出判断并回收，全局比较难，因此应避免全局变量

	   标记清除算法：js最常见的垃圾回收方式，当变量进入执行环境的时候，比如函数中声明一个变量，垃圾回收器将他标记为'进入环境'，
			 当变量离开（函数执行完后），就其标记为'离开环境'。垃圾回收器会在运行的时候给存储在内存中的所有变量加上标记，
			 然后去掉环境中的变量以及被环境中该变量所引用的变量（闭包）。在这些完成之后仍存在标记的就是要删除的变量了

十九、渐进增强和优雅降级
	1.渐进增强就是针对低版本浏览器进行构建页面，保证最基本的功能，然后对高级浏览器进行效果、交互等改进和最佳功能达到更好的用户体验
	2.优雅降级：一开始构建完整的功能，然后对低版本的进行兼容

二十、undefined 和 null
	1.undefined类型只要一个，即undefined，当声明变量还未被初始化时就是undefined
	2.null类型也只有一个值，即null。null用来表示尚未存在的对象，常用来表示函数企图返回一个不存在的对象
	3.NaN 与任何值都是相比较的结果都是false

二十一、valueof和tostring
	valueof：所有对象都有valueof，如果存在任意原始值，他就默认将对象转化为表示它的原始值。
				      如果对象是复合值，而却大部分对象无法真正表示一个原始值，因此默认的valueof()方法简单的返回对象本身，而不是返回原始值。
				      数组、函数和正则表达式简单的继承了这个more方法，返回对象本身
	
二十二、输入框的change和input事件
	onchange事件：要在input失去焦点的时候才触发
	oninput事件：要在用户输入的时触发，他是元素值发生变化时立即触发

二十三、同步和异步
	同步：由于js单线程，同步任务都在主线程上排队执行，前面任务没有执行完成，后面的任务会一直等待
	异步：不进入主线程，进入任务队列，等待主线程任务执行完成，开始执行。最基本的异步操作SetTimemot和SetInterval,等待主线程任务执行完，在开始执行里面的函数


二十四、函数的柯里化
	 概念：一个函数接受函数A作为参数，运行后返回return function一个新的函数，并且可以处理A中的参数（只接受单一参数的函数）
	 意义：将函数完全变成了接受一个参数，返回一个参数的固定形式，便于讨论和优化

二十五、while
	while循环会在指定条件为真时循环执行代码

二十六、TypeScript的优点：
      1、编译时的强类型，变成了强类型语言，还是编译成js 编译的时候就可以检验
      2、更好的模块化
      3、更好的是实现面向对象的编程，类、接口、模块

二十七、js的阻塞特性：所有浏览器在下载JS的时候，会阻止一切其他活动，比如其他资源的下载，内容的呈现等等。
		      直到JS下载、解析、执行完毕后才开始继续并行下载其他资源并呈现内容。
		      为了提高用户体验，新一代浏览器都支持并行下载JS，但是JS下载仍然会阻塞其它资源的下载（例如.图片，css文件等）。
	css阻塞：因为浏览器会维持html中css和js的顺序，样式表必须在嵌入的JS执行前先加载、解析完。
		 而嵌入的JS会阻塞后面的资源加载，所以就会出现上面CSS阻塞下载的情况。
	
二十八、meta元素可提供有关页面的元信息，比如针对搜索引擎和更新频度的描述和关键词
	meta name="keyword" 告诉搜素引擎网页的关键词
	meta name="description" 告诉搜素引擎站点的内容
	mata name="author" content="name"站点制作望着
	meta name="viewport" content="width=device-width, initial-scale=1.0 响应式页面					

二十九、splice和slice、map和forEach、 filter()、reduce()的区别
	 1.slice(start,end):方法可以从已有数组中返回选定的元素，返回一个新数组，包含从start到end（不包含该元素）的数组方法
		注意：该方法不会更新原数组，而是返回一个子数组
	 2.splice():该方法想或者从数组中添加或删除项目，返回被删除的项目。（该方法会改变原数组）
		splice(index, howmany,item1,...itemx)
			·index参数：必须，整数规定添加或删除的位置，使用负数，从数组尾部规定位置
			·howmany参数：必须，要删除的数量，
			·item1..itemx:可选，向数组添加新项目
	3.map()：会返回一个全新的数组。使用于改变数据值的时候。会分配内存存储空间数组并返回，forEach（）不会返回数据
	4.forEach(): 不会返回任何有价值的东西，并且不打算改变数据，单纯的只是想用数据做一些事情，他允许callback更改原始数组的元素
	5.reduce(): 方法接收一个函数作为累加器，数组中的每一个值（从左到右）开始缩减，最终计算一个值，不会改变原数组的值
	6.filter(): 方法创建一个新数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。它里面通过function去做处理	



							node面试
一、koa中间件执行机制
	1.添加中间件的方式是使用Koa实例的use方法，并传入一个generator函数，这个generator函数接受一个next参数
	2.use的原理：function Application () {this.middleware = [] // 这个数组就是用来装一个个中间间的}
	3.每次执行use方法，就把外面传进来的generator函数push到middleware数组中
		app.use = function (fn) {this.middleware.push(fn)}
	4.koa中是预先通过use方法，将请求可能会经过的中间间装在一个数组中。
	5.callback函数就是请求到来的时候执行的回调。把装着中间件middleware的数组作为参数传递为compose这个方法。
	6.componse把毫无关系的一个个中间件给收尾串起来了，就好比我们平常的烤面筋
	7.componse将中间件从最后一个开始处理，并一直往前知道第一个中间件。其实最关键的就是将最后一个中间件得到generator
	   作为参数传递给前一个中间件。当最后一个中间件的参数next是空的generator函数生成对象

	中间件是怎么跑起来的：https://juejin.im/post/591c8b4544d904006c90a2cb


二、koa和express的区别
	1.异步流程的控制。express采用callback来处理异步，koa2采用的是async/await
	2.错误处理。express采用callback捕获异常，对深层次的异常捕获不了。koa采用try/catch							


								vue面试
一、介绍下MVVM(数据的双向绑定）
	M: model数据模型
	V: view 界面
	MV:作为桥梁负责沟通view跟model
     只关心数据的流传，减少强耦合性。最关键的就是数据的双向绑定
 关键步骤：1.实现数据监听器Observer，用object.defineProperty()重写数据的get/set。值更新就在set中通知订阅者更新数据
	  2.实现模板编译compile，深度遍历dom树，对每个元素节点的指令模板替换数据以及订阅数据
	  3.实现watch用于连接Observer和compile，能够订阅并接受每一个属性的变动的通知，执行指令绑定的相应的回调函数，从而更新数据

mvc和mvvm其实区别并不大。都是一种设计思想。主要就是mvc中Controller演变成mvvm中的viewModel。mvvm主要解决了mvc中大量的DOM 操作使页面渲染性能降低，
加载速度变慢，影响用户体验。和当 Model 频繁发生变化，开发者需要主动更新到View 。

二、 eventBus vuex
 	原理：eventbus 解决了兄弟组件之间事件传递问题,本质是订阅发布者模式，从而摆脱了兄弟之间需要父组件转而传递的复杂。还有一种方法是vuex数据流，单一状态树,rootState树根
              名词，专车。订阅者跟发布者都引用专车，这个vue实例，来完成订阅发布者。 emit（发布）  on(订阅一个组件)
 npm包	vue-event-proxy

	vuex 是将数据单独的抽离出来，一种状态管理工具，它借鉴的是Flux、redux的基本思想，将转态抽离到全局形成一个store

三、watch:
	对属性进行监听，允许我们执行异步操作，限制我们执行该操作的频率（debounce），并在我们得到结果前，设置中间转态。

四、Vue的双向数据绑定实现原理
	1.核心就是数据劫持 + 发布/订阅者模式：vue使用的是Object.defineProperty()通过监听他的get/set事件，监听对数据的操作，从而触发数据同步

 Object.defineProperty缺陷的：
	1.只能对属性进行数据劫持，并且需要深度遍历整个对象
	2.对于数组不能监听数据的变化
    而proxy原生支持监听数组的变化，并且可以直接对整个对象进行拦截，所有Vue在下个版本中用proxy替换object.defineProperty


五、nextTick原理
 
六、生命周期函数  https://juejin.im/post/5b41bdef6fb9a04fe63765f1
		new Vue（创建一个Vue对象）--> beforeCreate --> observer Data(开始监控data对象数据变化） --> init event(vue内部初始化事件）

		 --> created()  --> compile(编译模板,把data里面的数据和模板生成html)  -->  beforeMount(还没有生成HTML到元素上)  -->
		
		 mounted(挂载完成，也就是模板中的html渲染到了html页面中）  -->  beforeUpdate (Vritual Dom)  --> updated  --> beforeDestroy --> destroyed	

	1.ajax请求最好放在created里面，页面可以访问到this了
	2.关于dom的操作要放在mounted里面，在mounted前面还没有生成dom
	3.每次进入/离开组件都要做一些事情，用什么钩子函数：
		不缓存：进入的时候可以用created和mounted钩子，离开的时候可以使用beforedDestory（可以访问this）和destoryed


		缓存：缓存了组件之后，再次进入组件不会触发beforeCreate，created, beforeMount,mounted
		      如果你想每次进入组件都做一些事情的话，你可以放在activated进入缓存组件的钩子中
七、keep-alive
	在被keep-alive包含的组件/路由，会多出两个生命周期：activated 和 deactivated
	actived在组件第一次渲染时会被调用，之后再每次缓存组件被激活时调用 调用机制：第一次进入缓存路由/组件，在mounted后面，beforeRouteEnter守卫传给 next 的回调函数之前调用：

八、Vue的SPA 如何优化加载速度
	1.减少入口文件体积
	2.静态资源本地缓存
	3.开启Gzip压缩
	4.使用SSR,nuxt.js

九、模块化
	基本概念： 1.在js中，一个模块就是实现特定功能的文件(js文件) 
		   2.遵循模块的机制，想要什么就加载什么模块
		   3.模块化开发需要遵循规范

	js实现模块化规范
		    1.AMD 浏览器  requirejs  模块被异步加载，模块加载不影响后面语句的运行 默认使用baseURL+ paths的路经解析方式
		    2.CommonJS  nodejs  
		    3.ES6的import/export
		    4.CMD 浏览器端 

	解决的问题：1.命名冲突 2.文件依赖 3.模块的复用 4.统一规范和开发方式

十、谈谈Vue和React组件化的思想
	1.我们在各个页面开发的时候，会产生很多重复的功能，比如element中的xxxx。像这种纯粹非页面的UI，便成为我们常用的UI组件，最初的前端组件也就仅仅指的是UI组件
	2.随着业务逻辑变得越来多是，我们就想要我们的组件可以处理很多事，这就是我们常说的组件化，这个组件就不是UI组件了，而是包具体业务的业务组件
	3.这种开发思想就是分而治之。最大程度的降低开发难度和维护成本的效果。并且可以多人协作，每个人写不同的组件，最后像撘积木一样的把它构成一个页面	

十一、vue的依赖收集和watch原理
	

							
							React
一、react和vue的区别
       =>  相同点：
		1.数据驱动页面，提供响应式的试图组件
		2.都有virtual DOM,组件化的开发，通过props参数进行父子之间组件传递数据，都实现了webComponents规范
		3.数据流动单向，都支持服务器的渲染SSR
		4.都有支持native的方法，react有React native， vue有wexx
	=>  不同点：
		1.数据绑定：Vue实现了双向的数据绑定，react数据流动是单向的
		2.数据渲染：大规模的数据渲染，react更快
		3.使用场景：React配合Redux架构适合大规模多人协作复杂项目，Vue适合小快的项目
		4.开发风格：react推荐做法jsx + inline style把html和css都写在js了
			    vue是采用webpack + vue-loader单文件组件格式，html, js, css同一个文件

二、redux中的reducer（纯函数）
	Redux数据流里，reduces其实是根据之前的状态（previous state）和现有的action（current action）更新state(这个state可以理解为上下累加器的结果）
	每次redux reducer被执行时，state和action被传入，这个state根据action进行累加或者是'自身消减'(reduce),进而返回最新的state,这也就是典型reduce函数的用法：state ->  action ->  state

三、react的refs
	refs就想一个逃生窗，允许我们之间访问dom元素或者组件实例，可以向组件添加一个ref属性的值是一个回调函数，
	它将接受地城dom元素或组件的已挂在实例，作为第一个参数

四、react中的keys
	帮组我们跟踪哪些项目已更改、添加、从列表中删除，key是独一无二的，可以让我们高效的去定位元素，并且操作它

五、React的生命周期
	三个状态：Mounting(已插入真实的DOM）
		  Updating(正在被重新渲染)
		  Unmounting(已移除真实的DOM)
	componentDIdMount 在第一次渲染后调用，只在客服端。之后组件已经生成对应的DOM结构，
	componentDidUpdate 在组件完成更新后立即调用，在出初始化是不会调用

六、React子组件向父组件传值
	父组件通过props 给子组件传递数据，子组件则是通过调用父组件传给它的函数给父组件传递数据。

七、React数据流

八、为什么虚拟DOM会提高性能 https://www.zhihu.com/question/29504639?sort=created
	虚拟DOM相当于在js和真实dom中间加了一个缓存，利用dom diff算法避免了没有必要的doom操作，从而提高性能
	具体实现步骤：
		·用JavaScript对象结构表示DOM树的结构；然后用这个树构建一个真正的DOM树，插到文档中
	        ·当状态变更的时候，重新构造一棵树的对象树，然后用新的树和旧的树进行对比，记录两棵树差异
		·把2所记录的差异应用到步骤1所构建的真正的DOM树上，试图就更新了。

九、diff算法
	1.把树形结构按照层级分解，只比较同级元素
	2.给列表结构的每个单元添加key属性，方便比较。在实际代码中，会对新旧两棵树进行一个深度优先的遍历，这样每个节点都会有一个标记
	3.在深度优先遍历的时候，每遍历到一个节点就把该节点和新的树进行对比。如果有差异的话就记录到一个对象里面
	Vritual DOM 算法主要实现上面步骤的三个函数：element， diff， patch。然后就可以实际的进行使用
	react只会匹配相同的class的component（这里的class指的是组件的名字）
	合并操作，条用component的setState方法的时候，React将其标记为dirty.到每一个时间循环借宿，React检查所有标记dirty的component重新绘制
	4.选择性子树渲染。可以重写shouldComponentUpdate提高diff的性能	

十、super

十一、简述下flux的思想
	flux的最大特点，就是数据的‘单向流动’
	1.用户访问View
	2.View发出用户的Action
	3.Dispatcher收到Action,要求state进行相应的更新
	4.store更新后，发出一个‘change’事件后，更新页面

十二、reac性能优化是哪个周期函
	shouldComponentUpdate 这个方法用来判断是否需要调用render方法重新描绘dom.因为dom的描绘非常消耗性能，
	如果我们在shouldComponentUpdate方法中能够写出更优化的dom diff算法，可以极大的提高性能

十三、react怎么划分业务组件和技术组件
	根据组件的职责通常把组件分为UI组件和容器组件
	UI组件负责UI的呈现，容器组件负责管理数据和逻辑
	两者通过React-redux提供connect方法联系起来

十四、setState
	setState通过一个队列机制实现state更新，当执行setState时，会将需要更新的state很后放入状态队列
	而不会立即更新this.state，队列机制可以高效地批量更新state。如果不通过setState而直接修改this.state的值	
	那么该state将不会被放入状态队列中。当下次调用setState并对状态队列进行合并时，就会忽略之前修改的state，造成不可预知的错误
	
	同时，也利用了队列机制实现了setState的异步更新，避免了频繁的重复更新state

	同步更新state:
		setState 函数并不会阻塞等待状态更新完毕，因此 setNetworkActivityIndicatorVisible 有可能先于数据渲染完毕就执行。第二个参数是一个回调函数，在setState的异步操作结束并且组件已经重新渲染的时候执行
		也就是说，我们可以通过这个回调来拿到更新的state的值，实现代码的同步
	
	例子：componentDidMount() {
    
		fetch('https://test.com')
        
		.then((res) => res.json())
        
		.then(
(data) => {
this.setState({ data:data });

				StatusBar.setNetworkActivityIndicatorVisible(false);
            }
   
							
						性能优化

一、webpack打包文件体积过大？（最终打包为一个js文件）
	1.异步加载模块
	2.提取第三库
	3.代码压缩
	4.去除不必要的插件

如何优化webpack构建的性能
	一、减少代码体积 1.使用CommonsChunksPlugin 提取多个chunk之间的通用模块，减少总体代码体积
			 2.把部分依赖转移到CDN上，避免每次编译过程都由Webpack处理
			 3.对一些组件库采用按需加载，避免无用的代码
	二、减少目录检索范围
			 ·在使用loader的时候，通过制定exclude和include选项，减少loader遍历的目录范围，从而加快webpack编译速度
		
	三、减少检索路经：resolve.alias可以配置webpack模块解析的别名，对于比较深的解析路经，可以对其配置alias


二、我们把开发中的所有资源（图片，js、css文件）都看成模块，通过loader和plugins来对资源进行处理，打包成符合生产环节部署的前端资源。
							
三、移动端的性能优化
      1、首屏加载和按需加载，懒加载
      2、资源预加载
      3、图片压缩处理，使用base64内嵌图片
      4、合理缓存dom对象
      5、使用touchstart代替click（click 300毫秒的延迟）
      6、利用transform:translateZ(0)，开启硬件GUP加速
      7、不滥用web字体，不滥用float（布局计算消耗性能），减少font-size声明
      8、使用viewport固定屏幕渲染，加速页面渲染内容
      9、尽量使用事件代理，避免直接事件绑定

四、Vue的SPA 如何优化加载速度
	1.减少入口文件体积
	2.静态资源本地缓存
	3.开启Gzip压缩
	4.使用SSR,nuxt.js

五、移动端300ms延迟
	由来：300毫米延迟解决的是双击缩放。双击缩放，手指在屏幕快速点击两次。safari浏览器就会将网页缩放值原始比例。
	     由于用户可以双击缩放或者是滚动的操作，当用户点击屏幕一次之后，浏览器并不会判断用户确实要打开至这个链接，还是想要进行双击操作
	    因次，safair浏览器就会等待300ms，用来判断用户是否在次点击了屏幕
	解决方案：1.禁用缩放，设置meta标签 user-scalable=no
		  2.fastclick.js
			原理：FastClick的实现原理是在检查到touchend事件的时候，会通过dom自定义事件立即
			      发出click事件，并把浏览器在300ms之后真正的click事件阻止掉
	fastclick.js还可以解决穿透问题

六、页面的重构；在不改变外部行为的前提下，简化结构、添加可读性

							服务器端
一、状态码：

      2XX（成功处理了请求状态）
          200 服务器已经成功处理请求，并提供了请求的网页
          201 用户新建或修改数据成功
          202 一个请求已经进入后台
          204 用户删除成功
      3XX（每次请求使用的重定向不要超过5次）
          304 网页上次请求没有更新，节省带宽和开销
      4XX（表示请求可能出错，妨碍了服务器的处理）
          400 服务器不理解请求的语法
          401 用户没有权限（用户名，密码输入错误）
          403 用户得到授权（401相反），但是访问被禁止
          404 服务器找不到请求的网页，
      5XX（表示服务器在处理请求的时候发生内部错误）
          500 服务器遇到错误，无法完成请求
          503 服务器目前无法使用（超载或停机维护）

二、304的缓存原理（添加Etag标签.last-modified） 304 网页上次请求没有更新，节省带宽和开销
	1.服务器首先产生Etag,服务器可在稍后使用它来判断页面是否被修改。本质上，客户端通过该记号传回服务器要求服务器验证（客户端）缓存）
	2.304是	HTTP的状态码，服务器用来标识这个文件没有被修改，不返回内容，浏览器接受到这个状态码会去去找浏览器缓存的文件
	3.流程：客户端请求一个页面A。服务器返回页面A，并在A上加一个Tage客服端渲染该页面，并把Tage也存储在缓存中。客户端再次请求页面A
		并将上次请求的资源和ETage一起传递给服务器。服务器检查Tage.并且判断出该页面自上次客户端请求之后未被修改。直接返回304
	
	last-modified: 客服端请求资源，同时有一个last-modified的属性标记此文件在服务器最后修改的时间
			客服端第二次请求此url时，根据http协议。浏览器会向服务器发送一个If-Modified-Since报头，
			询问该事件之后文件是否被修改，没修改返回304

	 有了Last-Modified，为什么还要用ETag？
      1、因为如果在一秒钟之内对一个文件进行两次更改，Last-Modified就会不正确（Last—Modified不能识别秒单位的修改）
      2、某些服务器不能精确的得到文件的最后修改时间
      3、一些文件也行会周期新的更改，但是他的内容并不改变（仅仅改变修改的事件），这个时候我们并不希望客户端认为文件被修改，而重新Get
    
    ETag，为什么还要用Last-Modified？
      1、两者互补，ETag的判断的缺陷，比如一些图片等静态文件的修改
      2、如果每次扫描内容都生成ETag比较，显然要比直接比较修改时间慢的多。


    ETag是被请求变量的实体值（文件的索引节，大小和最后修改的时间的Hash值）
      1、ETag的值服务器端对文件的索引节，大小和最后的修改的事件进行Hash后得到的。

三、get/post的区别
	1.get数据是存放在url之后，以？分割url和传输数据，参数之间以&相连； post方法是把提交的数据放在http包的Body中
	2.get提交的数据大小有限制，（因为浏览器对url的长度有限制），post的方法提交的数据没有限制
	3.get需要request.queryString来获取变量的值，而post方式通过request.from来获取变量的值
	4.get的方法提交数据，会带来安全问题，比如登录一个页面，通过get的方式提交数据，用户名和密码就会出现在url上

四、http协议的理解
	1.超文本的传输协议，是用于从万维网服务器超文本传输到本地资源的传输协议
	2.基于TCP/IP通信协议来传递数据（HTML，图片资源）
	3.基于运用层的面向对象的协议，由于其简洁、快速的方法、适用于分布式超媒体信息系统
	4.http请求信息request：
		请求行（request line）、请求头部（header）,空行和请求数据四部分构成

		请求行，用来说明请求类型,要访问的资源以及所使用的HTTP版本.
		请求头部，用来说明服务器要使用的附加信息
		空行，请求头部后面的空行是必须的
		请求数据也叫主体，可以添加任意的其他数据。
	5.http相应信息Response
		状态行、消息报头、空行和响应正文

		状态行，由HTTP协议版本号， 状态码， 状态消息 三部分组成
		消息报头，用来说明客户端要使用的一些附加信息
		空行，消息报头后面的空行是必须的
		响应正文，服务器返回给客户端的文本信息。


五、http和https
	https：是以安全为目标的HTTP通道，简单讲是HTTP的安全版本，通过SSL加密
	http：超文本传输协议。是一个客服端和服务器端请求和应答的标准（tcp）,使浏览器更加高效，使网络传输减少

五、http1.0 1.1 2.0的区别
	长连接：HTTP1.0需要使用keep-alive参数来告知服务器建立一个长连接，而HTP1.1默认支持长连接
	节约宽带：HTTP1.1支持只发送一个header信息（不带任何body信息）
	host域（设置虚拟站点，也就是说，web server上的多个虚拟站点可以共享同一个ip端口）：HTTP1.0没有host域

	1.http2采用的二进制文本传输数据，而非http1文本格式，二进制在协议的解析和扩展更好
	2.数据压缩：对信息头采用了HPACK进行压缩传输，节省了信息头带来的网络流量
	3.多路复用：一个连接可以并发处理多个请求
	4.服务器推送：我们对支持HTTP2.0的web server请求数据的时候，服务器会顺便把一些客户端需要的资源一起推送到客户端，免得客户端再次创建连接发送请求到服务器端获取。这种方式非常合适加载静态资源

七、web缓存
	1.web缓存就是存在于客户端与服务器之间的一个副本、当你第一个发出请求后，缓存根据请求保存输出内容的副本
	2.缓存的好处
            （1）减少不必要的请求
	    （2）降低服务器的压力，减少服务器的消耗
	    （3）降低网络延迟，加快页面打开速度（直接读取浏览器的数据）

八、常见的web安全及防护原理
	1.sql注入原理：通郭sql命令插入到web表单递交或者输入活命，达到欺骗服务器执行的恶意sql命令
			防范：1.对用户输入进行校验
			       2.不适用动态拼接sql
	2.XSS（跨站脚本攻击）：往web页面插入恶意的html标签或者js代码。
			        举例子：在论坛放置一个看是安全的链接，窃取cookie中的用户信息
				防范：1.尽量采用post而不使用get提交表单
				      2.避免cookie中泄漏用户的隐式
	3.CSRF(跨站请求伪装）：通过伪装来自受信任用户的请求
				举例子：黄轶老师的webapp音乐请求数据就是利用CSRF跨站请求伪装来获取QQ音乐的数据
				防范：在客服端页面增加伪随机数，通过验证码
	XSS和CSRF的区别：
	   1.XSS是获取信息，不需要提前知道其他用户页面的代码和数据包
	   2.CSRF代替用户完成指定的动作，需要知道其他页面的代码和数据包

九、CDN（内容分发网络）
	1.尽可能的避开互联网有可能影响数据传输速度和稳定性的瓶颈和环节。使内容传输的更快更稳定。
	2.关键技术：内容存储和分发技术中
	3.基本原理：广泛采用各种缓存服务器，将这些缓存服务器分布到用户访问相对的地区或者网络中。当用户访问网络时利用全局负载技术
		    将用户的访问指向距离最近的缓存服务器，由缓存服务器直接相应用户的请求（全局负载技术）

十、TCP三次握手	(客服端和服务器端都需要确认各自可收发）
	客服端发c起请求连接服务器端s确认，服务器端也发起连接确认客服端确认。
	第一次握手：客服端发送一个请求连接，服务器端只能确认自己可以接受客服端发送的报文段
	第二次握手： 服务端向客服端发送一个链接，确认客服端收到自己发送的报文段
	第三次握手： 服务器端确认客服端收到了自己发送的报文段

十一、从输入url到获取页面的完整过程  https://blog.csdn.net/samjustin1/article/details/52650520
	1.查询NDS(域名解析),获取域名对应的IP地址  查询浏览器缓存
	2.浏览器与服务器建立tcp链接（三次握手）
	3.浏览器向服务器发送http请求(请求和传输数据）
	4.服务器接受到这个请求后，根据路经参数，经过后端的一些处理生成html代码返回给浏览器
	5.浏览器拿到完整的html页面代码开始解析和渲染，如果遇到外部的css或者js，图片一样的步骤
	6.浏览器根据拿到的资源对页面进行渲染，把一个完整的页面呈现出来

十二、浏览器渲染原理及流程 DOM -> CSSOM -> render -> layout -> print
	流程：解析html以及构建dom树 -> 构建render树 ->  布局render树 -> 绘制render树
	概念：1.构建DOM树： 渲染引擎解析HTML文档，首先将标签转换成DOM树中的DOM node(包括js生成的标签)生成内容树
	      2.构建渲染树： 解析对应的css样式文件信息（包括js生成的样式和外部的css）
	      3.布局渲染树：从根节点递归调用，计算每一个元素的大小，位置等。给出每个节点所在的屏幕的精准位置
	      4.绘制渲染树：遍历渲染树，使用UI后端层来绘制每一个节点
   
	重绘：当盒子的位置、大小以及其他属性，例如颜色、字体大小等到确定下来之后，浏览器便把这些颜色都按照各自的特性绘制一遍，将内容呈现在页面上
		触发重绘的条件：改变元素外观属性。如：color，background-color等
		重绘是指一个元素外观的改变所触发的浏览器行为，浏览器会根据元素的新属性重新绘制，使元素呈现新的外观
	注意：table及其内部元素需要多次计算才能确定好其在渲染树中节点的属性值，比同等元素要多发时间，要尽量避免使用table布局
	
	重排（重构/回流/reflow）： 当渲染书中的一部分（或全部）因为元素的规模尺寸，布局，隐藏等改变而需要重新构建，这就是回流。
		每个页面都需要一次回流，就是页面第一次渲染的时候

	重排一定会影响重绘，但是重绘不一定会影响重排


十三、为什么css放在顶部而js写在后面
	1.浏览器预先加载css后，可以不必等待HTML加载完毕就可以渲染页面了
	2.其实HTML渲染并不会等到完全加载完在渲染页面，而是一边解析DOM一边渲染。
	3.js写在尾部，主要是因为js主要扮演事件处理的功能，一方面很多操作是在页面渲染后才执行的。另一方面可以节省加载时间，使页面能够更加的加载，提高用户的良好体验

	但是随着JS技术的发展，JS也开始承担页面渲染的工作。比如我们的UI其实可以分被对待，把渲染页面的js放在前面，时间处理的js放在后面

十四、存储方式与传输方式
	1.indexBD: 是h5的本地存储库，把一些数据存储到浏览器中，没网络，浏览器可以从这里读取数据，离线运用。5m
	2.Cookie: 通过浏览器记录信息确认用户身份，最大4kb,这也就限制了传输的数据，请求的性能会受到影响
	3.Session: 服务器端使用的一种记录客户状态的机制（session_id存在set_cookie发送到客服端，保存为cookie）
	4.localStroage: h5的本地存储，数据永久保存在客服端

    1、cookie，sessionStorage，localStorage是存放在客户端，session对象数据是存放在服务器上
       实际上浏览器和服务器之间仅需传递session id即可，服务器根据session-id找到对应的用户session对象
        session存储数据更安全一些，一般存放用户信息，浏览器只适合存储一般的数据
    2、cookie数据始终在同源的http请求中携带，在浏览器和服务器来回传递，里面存放着session-id
       sessionStorage，localStorage仅在本地保存
    3、大小限制区别，cookie数据不超过4kb，localStorage在谷歌浏览中2.6MB
    4、数据有效期不同，cookie在设置的（服务器设置）有效期内有效，不管窗口和浏览器关闭
      sessionStorage仅在当前浏览器窗口关闭前有效，关闭即销毁（临时存储）
      localStorage始终有效	


SessionStorage和localStorage区别：
	1.sessionStorage用于本地存储一个会话（session）中的数据，这些数据只有在用一个会话的页面中才能被访问（也就是说在第一次通信过程中）
	   并且在会话结束后数据也随之销毁，不是一个持久的本地存储，会话级别的储存
	2.localStorage用于持久化的本地存储，除非主动删除数据，否则不会过期

token、cookie、session三者的理解？？？！！！
    1、token就是令牌，比如你授权(登录)一个程序时,他就是个依据,判断你是否已经授权该软件（最好的身份认证，安全性好，且是唯一的）
        用户身份的验证方式    

    2、cookie是写在客户端一个txt文件，里面包括登录信息之类的，这样你下次在登录某个网站，就会自动调用cookie自动登录用户名
        服务器生成，发送到浏览器、浏览器保存，下次请求再次发送给服务器（存放着登录信息）

    3、session是一类用来客户端和服务器之间保存状态的解决方案，会话完成被销毁（代表的就是服务器和客户端的一次会话过程）
        cookie中存放着sessionID，请求会发送这个id。sesion因为request对象而产生。
  

    基于Token的身份验证：（最简单的token: uid用户唯一的身份识别 + time当前事件戳 + sign签名）
      1、用户通过用户名和密码发送请求
      2、服务器端验证
      3、服务器端返回一个带签名的token，给客户端
      4、客户端储存token，并且每次用于发送请求
      5、服务器验证token并且返回数据
      每一次请求都需要token

    cookie与session区别
      1、cookie数据存放在客户的浏览器上，session数据放在服务器上。
      2、cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗考虑到安全应当使用session。
      3、session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能考虑到减轻服务器性能方面，应当使用COOKIE。
      4、单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。

    session与token区别
      1、session认证只是把简单的User的信息存储Session里面，sessionID不可预测，一种认证手段。只存在服务端，不能共享到其他的网站和第三方App
      2、token是oAuth Token，提供的是认证和授权，认证针对用户，授权是针对App，目的就是让某APP有权访问某用户的的信息。Token是唯一的，
         token不能转移到其他的App，也不能转到其他用户上。（适用于App）
      3、session的状态是存在服务器端的，客户端只存在session id， Token状态是存储在客户端的

    Cookie的弊端有哪些？？？（优势：保存客户端数据，分担了服务器存储的负担）
      1、数量和长度的限制。每个特定的域名下最多生成20个cookie（chorme和safari没有限制）
      2、安全性问题。

						设计模式

一、观察者模式：https://juejin.im/post/5a14e9edf265da4312808d86   https://juejin.im/post/5af05d406fb9a07a9e4d2799
	在软件开发设计中是一个对象(subject)，维护一系列依赖他的对象（observer），当任何状态发生改变自动通知他们。强依赖关系
	简单理解：数据发生改变时，对应的处理函数就会自动执行。一个Subjet,用来维护Observers,为某些event来通知（notify）观察者

二、发布-订阅者  有一个信息中介，过滤 耦合性低
	它定义了一种一对多的关系，可以使多个观察者对象对一个主题对象进行监听，当这个主题对象发生改变时，依赖的所有对象都会被通知到。

两者的区别：
	1.观察者模式中，观察者知道Subject ,两者是相关联的，而发发布订阅者只有通过信息代理进行通信
	2.在发布订阅模式中，组件式松散耦合的。正好和观察者模式相反。
	3.观察者大部分是同步的，比如事件的触发。Subject就会调用观察者的方法。而发布订阅者大多数是异步的（）
	4.观察者模式需要在单个应用程序地址空间中实现，而发布订阅者更像交叉应用模式。

1004001111
						 	数据结构和算法

一、两个栈实现一个队列，两个队列实现一个栈 https://www.cnblogs.com/MrListening/p/5697459.html

二、红黑树（解决二叉树依次插入多个节点时的线型排列） https://juejin.im/post/5a27c6946fb9a04509096248

三、最小栈的实现（查找最小元素，用两个栈配合栈内元素的下标）https://juejin.im/post/5a2ff8c651882533d0230a85

四、十大排序 
	1.冒泡排序：重复走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把它们交换过来。
	  实现过程：1.比较相邻的元素。如果第一个比第二个大，就交换他们两个
		    2.对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对，这样在最后的元素应该会是最大的数
		    3.针对所有的元素重复以上的步骤，除了最后一个
		    4.重复步骤1-3，直到排序完成。
	2.选择排序：首先在未排序序列中找到最小值，放在排序序列的起始位置，然后，在从剩下未排序元素中继续寻找最小值，然后放在与排序序列的末尾
	  实现过程：

	3.插入排序：构建有序序列，对于未排序数据，在已排序序列中冲后向前扫描，找到相应位置并插入
	  实现过程：1.从第一个元素开始，该元素可以认为已经被排序
		    2.取出下一个元素，在已排序的元素序列中冲后向前扫描
		    3.如果该元素（以排序）大于新元素，将元素向后移一位
		    4.在取出一个元素，比较之前的，直到找到自己合适的位置

	4.桶排序：将数据分布到有限数量的桶里，每个桶在分别排序

	1.快速排序：快速排序使用分治法把一个串（list）分为两个子串（sub-lists）.具体算法实现
	  实现过程：1.从数组中挑出一个元素，成为一个基准
		    2.重新排列数组，所有元素比基准小的摆在基准前面，所有元素比基准大的摆在基准后面（相同的可以摆在一边）
			这个分区退出之后，该基准就处于数列的中间位置。成为分区操作。
		    3.递归的把小于基准值的子数列和大于基准值元素的子数列排序
	算法实现： function quickSort (arr) {
			if （arr.length <= 1） {return arr}
			var destIndex = Math.floor(arr.length/2)
			var left = [], right = [];
			var dest = arr.splice(destIndex,1)[0];
			for (var i =0;i<arr.length;i++){
				if (arr[i]<dest) {
				left.push(arr[i])
				} else {
				right.push(arr[i]) }
			return quickSort(left).concat([dest],quickSort(right)
				

	2.堆排序：利用对这种数据结构所涉及的一种排序算法，堆积是一个近乎完全二叉树的结构，并同时满足堆积的性质：即子节点的键值或索引总是小于（或大于）它的父节点。
	  实现过程：1.

五、数组去重 https://juejin.im/post/5aed6110518825671b026bed#heading-6 
	1.双重循环
	2.indexOf
	3.数组排序去重 最快你Olong
	
六、字符串
	判断回文字符串：（递归的思想）
		1.字符串分隔，倒转，聚合[...obj].reverse().join('')
		2.字符串头部和尾部，逐次向中间检测 
			实现：function isPalindrome(line) {
				line += '';
				for (var i=0,j=line.length-1;i<j;i++,j--) {
					if (line.chartAt(i) !== line.chartAt(j) {
					return false
				}
				
		3.递归

七、二分查找（有序数组的查找）
	 二分查找可以解决已排序数组的查找问题，即只要数组中包含T(要查找的值)，那么通过不断的缩小包含T的数据范围，就可以最终要找到的数
	 (1) 一开始,数据范围覆盖整个数组。
	 (2) 将数组的中间项与T进行比较，如果T比数组的中间项小，则到数组的前半部分继续查找，反之，则到数组的后半部分继续查找。
	 (3) 就这样，每次查找都可以排除一半元素，相当于范围缩小一半。这样反复比较，反复缩小范围，最终会在数组中找到T
	代码实现：function binarySearch (data, dest, start, end){
			var end = end || data.length-1;
			var start = start || 0;
			var m = Math.floor((start+end)/2);
			if (dest<data[m]){
				return binarySearch(data, dest, 0, m-1)
			} else {
				return binarySearch(data, dest, m+1, end)
			}}
			return false



							手写代码

一、动手实现一个bind（原理通过apply，call）
	一句话概括：1.bind()返回一个新函数，并不会立即执行。
		    2.bind的第一个参数将作为他运行时的this，之后的一系列参数将会在传递的实参前传入作为他的参数
		    3.bind返回函数作为构造函数，就是可以new的，bind时指定的this值就会消失，但传入的参数依然生效
Function.prototype.bind = function (obj, arg) {
   var arg = Array.prototype.slice.call(arguments, 1);
   var context = this;
   var bound = function (newArg) {
   arg = arg.concat(Array.prototype.slice.call(newArg);
   return context.apply(obj, arg)
}
  var F =  function () {}  // 在new一个bind会生成新函数，必须的条件就是要继承原函数的原型，因此用到寄生继承来完成我们的过程
  F.prototype = context.prototype;
  bound.prototype =  new F();
  return bound;
}	

二、 AJAX （异步的javascript和xml）
	ajax的原理：相当于在用户和服务器之间加一个中间层（ajax引擎),使用户操作与服务器响应异步化。
	优点：在不刷新整个页面的前提下与服务器通信维护数据。不会导致页面的重载
	      可以把前端服务器的任务转嫁到客服端来处理，减轻服务器负担，节省宽带
	劣势：不支持back。对搜索引擎的支持比较弱；不容易调试	
	怎么解决呢？通过location.hash值来解决Ajax过程中导致的浏览器前进后退按键失效，
	解决以前被人常遇到的重复加载的问题。主要比较前后的hash值，看其是否相等，在判断是否触发ajax
function getData(url) {
    var xhr = new XMLHttpRequest();  // 创建一个对象，创建一个异步调用的对象
    xhr.open('get', url, true)  // 设置一个http请求，设置请求的方式，url以及验证身份
    xhr.send() //发送一个http请求
    xhr.onreadystatechange = function () {  //设置一个http请求状态的函数
      if (xhr.readyState == 4 && xhr.status ==200) {
        console.log(xhr.responseText)  // 获取异步调用返回的数据
      }
    }
  }
  Promise(getData(url)).resolve(data => data)

	 AJAX状态码：0 - （未初始化）还没有调用send()方法
		     1 - （载入）已调用send方法，正在发送请求
		     2 - （载入完成呢）send()方法执行完成
		     3 - （交互）正在解析相应内容
		     4 - （完成）响应内容解析完成，可以在客户端调用了


三、函数节流（throttle）
 function throttle (func, wait) {
        var timeout;
        var previous = 0;
        return function () {
            context = this;
            args = arguments;
            if (!timeout) {
                timeout = setTimeout(() => {
                    timeout = null;
                    func.apply(context,args)
                }, wait);
            }
        }
    }
     
}

四、函数防抖（dobounce）
 function debounce (func, wait) {
         var timeout;
         return function() {
             var context = this;
             var args = arguments;
             clearTimeout(timeout);
             timeout = setTimeout(() => {
                 func.apply(context,args)
             }, wait);
         }
     }

五、实现一个函数clone，可以对JavaScript中的5种主要的数据类型（包括Number、String、Object、Array、Boolean）进行值复制
    
    Object.prototype.clone = function() {
      var newObject = this.constructor === Array ? [] : {}  //对象的深拷贝 获取对应的构造函数 [] 或者 {}
      for (let e in this) { //遍历对象的属性 in  this[e]
        newObject[e] = typeof this[e] === 'object' ? this[e].clone() : this[e]  //对象中的属性如果还是对象 那就继续递归 否则就返回基本的数据类型
      }
      return newObject
    }
 
六、实现一个简单的Promise https://juejin.im/post/5b2f02cd5188252b937548ab
class Promise {
  constructor (executor) {   // executor里面有两个参数，一个叫resolve（成功），一个叫reject（失败）。
    this.status = 'pending',
    this.value = undefined;
    this.reason = undefined;
    // 成功存放的数组
    this.onResolvedCallbacks = [];
     // 失败存放法数组
     this.onRejectedCallbacks = [];
    let resolve = (value) => {
      if (this.status == 'pending') {
        this.status = 'resolve';
        this.value = value;
        this.onResolvedCallbacks.forEach(fn => fn())
      }
    }

    let reject = (reason) => {
      if (this.status == 'pending') {
        this.status = 'reject';
        this.reason = reason;
        this.onRejectedCallbacks.forEach(fn => fn())
      }
    }
    try{
      executor(resolve, reject);
    } catch (err) {
      reject(err);
    }
  } 
  then (onFullFilled,onRejected) {
    if (this.status == 'resolved') {
      onFullFilled(this.value)
    }
    if (this.status == 'rejectd') {
      onRejected(this.reason);
    }
    if (this.status == 'pending') {
      this.onResolvedCallbacks.push(()=>{
        onFullFilled(this.value);
      })
      this.onRejectedCallbacks.push(()=> {
          onRejected(this.reason);
      })
  }
   
  }
}

const p = new Promise((resolve, reject) => {
  setTimeout(() => {
      resolve('hello world')
  }, 1000);
})
p.then((data) =>{
  console.log(data)
},(err) =>{
  console.log(err);
})

七、发布订阅者模式（观察者模式）

var event = {}; // 发布者
event.clientList = [] //发布者的缓存列表

event.listen = function (fn) {  // 增加订阅者函数
  this.clientList.push(fn)
}

event.trigger = function () {  // 发布信息
  for (var i =0;i<this.clientList.length;i++) {
    var fn = this.clientList[i];
    fn.apply(this, arguments);
  }
}

event.listen (function(time) {
  console.log('正式上班时间为：' +time)
})
event.trigger ('2018/7')

八、手动写一个node服务器
const http = require('http');
const fs = require('fs');
const server = http.createServer((req,res) => {
	if (reu.url == '/') {
	const indexFile = fs.createReadStream('./index.html')
	req.writeHead(200,{'context-Type':'text/html;charset = utf8})
	indexFile.pipe(res)
}
server.listen(8080)
