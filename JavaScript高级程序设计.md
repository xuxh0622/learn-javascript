##### 基本概念

> 变量省略var操作符的变量是全局变量，在函数中通过var定义的变量，在函数被调用时，创建该变量并为其赋值，函数执行完毕，立即销毁。数据类型：Undefined、Null、Boolean、Number、String六种基本类型，还有一个复杂数据类型Object。

```javascript
var message;
alert(message == undefined) //判断变量是否Undefined类型
alert(typeof message)  //未声明或未赋值，都是undefined类型
typeof message  //"undefined"--未定义&“boolean”--布尔值&“string”--字符串&“number”--数值&“object”对象或null&“function”--函数
alert(!!"blue")  //逻辑非操作用于将一个值转换为其对应的布尔值
alert(55 === "55")  //false类型不同，全等或不全等(!==)判断转换前两个数类型、值是否相同
```

##### 变量、作用域或内存问题

> 全局执行环境是最外围的一个执行环境，作为window对象的属性和方法。每个函数有自己的执行环境。代码执行会生成一个作用域链，开头是自己变量对象，然后外层环境一直到全局执行环境。作用域链本质是一个指向变量对象的指针列表，只引用但不实际包含变量对象。

window  //全局执行环境  
　|//-color  //变量对象  
　|//-changeColor()  //函数活动对象（arguments）作为变量对象  
　　　|//anotherColor  
　　　|//swapColor()  
　　　　　|//tempColor   //执行代码变量对象  
```javascript
alter(person instanceof Object)  //检查对象类型
```
#### 引用类型

###### 数组

```javascript
//创建数组
var colors = new Array();
var colors = new Array("red", "blue");
var colors = new Array(3);
var colors = ["red", "blue"];  //通过数组字面量表示法
//数组常用方法
alert(colors instanceof Array);
colors.push("black");  //最后插入一个字符串，长度加一
colors.pop();  //black最后一项弹出，长度减一
colors.shift();  //red最前面一个弹出，长度减一
colors.unshift("yellow");  //最前面插入，长度加一
colors.reverse();  //反转顺序
colors.sort();  //排序
colors.concat("yellow",["black"]);  //后面添加数组
colors.slice(1,4);  //截取数组
function compare(value1, value2){
  return value1 - value2;  //第一个参数位于第二个参数之前，返回负数
}
colors.sort(compare);
```

###### 函数

> Function类型，内部有两个对象arguments和this，有两个属性length（希望接收参数个数）和prototype。两个方法apply()和call()。call第后面传确切参数，apply传参数数组。还有bind方法，会创建一个函数实例。 

```javascript
var data = [{name: "Zachary"},{name: "Nicholas"}];  //[]数字字面量，{}对象字面量
//----------apply start---------
function sum(num1, num2){
  return num1 + num2;
}
function callSum1(num1, num2){
  return sum.apply(this, arguments);  //结果20，第一个参数是其中运行函数的作用域，第二个是参数数组
}
//----------apply end----------
//----------bid  start----------
window.color = "red";
var o = {color: "blue"};
function sayColor(){
  alert(this.color);
}
var objectSayColor = sayColor.bind(o);
objectSayColor();  //blue
//----------bin  end/----------
```

##### 面向对象的程序设计

> 每个函数（Person）都有一个原型对象参数（prototype），Person.prototype指向原型对象（Person Prototype），原型对象有constructor（Person.prototype.constructor）指向原对象（Person）。

```javascript
//对象字面量方式创建对象，也是单例模式
var person = {
  name: "Nicholas",
  sayName: function(){
  	alter(this.name);
  }
};  //变量声明分号结尾
person.name或person[name]  //访问
//构造函数模式用于定义实例属性，而原型模式用于定义方法和共享的属性
function Person(name, age){  //函数名本身就是变量
    this.name = name;
    this.age = age;
    this.friends = {"Shellby", "Court"};
}
Perosn.prototype = {
    constructor : Person,
    sayName : function(){
        alter(this.name);
    }
}
```

##### 函数表达式

> 函数声明、函数表达式和闭包区别与使用。

```javascript
//函数声明提升，执行代码之前会先读取函数声明，所以调用方法可以放在之前
function sayHi(){}
//函数表示式，创建一个匿名函数给变量，匿名函数有全局性
var sayHi = function(){}
//闭包，在一个函数内部创建另一个函数
//添加外面圆括号，类似一个函数表达式，可以跟着()调用方法
(function(){
  //这里是块级作用域
})();
```



