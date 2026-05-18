功能说明  
1. render  
render(template: String, data: Map[String, String]) -> String  
用于渲染模板字符串，支持变量替换和默认值。

示例用法：  
```moonbit
let template = "Hello, {{ name }}! Welcome to {{ place }}. Your code: {{ code | default('unknown') }}."
let data1 = { "name": "Alice", "place": "Wonderland" }
render(template, data1)
// 输出: Hello, Alice! Welcome to Wonderland. Your code: unknown.

let data2 = { "name": "Alice", "place": "Wonderland", "code": "A123" }
render(template, data2)
// 输出: Hello, Alice! Welcome to Wonderland. Your code: A123.

let data3 = { "place": "Moon", "code": "B456" }
render(template, data3)
// 输出: Hello, {{ name }}! Welcome to Moon. Your code: B456.
```


2. render_file  
render_file(input_path: String, data: Map[String, String]) -> Unit  
用于渲染文件内容并写回原文件。

示例用法：  
```moonbit
let data = { "name": "张三", "age": "18" }
render_file("template.txt", data)
// 假设 template.txt 内容为：名字是{{name}}年龄是{{age}}
// 渲染后 template.txt 内容变为：名字是张三年龄是18
```
---

主要特性：  
- 支持 {{变量}} 替换  
- 支持 {{变量 | default('默认值')}} 语法  
- 未知变量保留原样  
- 提供文件渲染接口

如需更多用法，请参考 src/lib/main.mbt 和 src/test/render_t.mbt 中的示例与测试用例。
