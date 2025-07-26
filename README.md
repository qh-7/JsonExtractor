# JsonExtractor
JsonExtractor 是一个应用于Burp Suite 的可视化JSON数据提取插件。其核心功能是对复杂、多层嵌套的JSON响应数据进行可视化自定义的处理，支持导出为表格（如Excel）。通过内置的树形视图与右键菜单，可实现对提取规则的快速、精确定义，无需手动编写复杂的路径或脚本

导出文件名为result.xlsx
<img width="1280" height="545" alt="image" src="https://github.com/user-attachments/assets/8e284280-986d-41b1-8754-9832c08859b1" />


2使用说明
将JSON数据复制到左侧点击分析
<img width="1280" height="211" alt="image" src="https://github.com/user-attachments/assets/1dce2431-09c2-4c19-811e-4f751eea423d" />

在右侧的JSON结构视图中，先右键配置数组节点为设为记录根路径
<img width="1280" height="483" alt="image" src="https://github.com/user-attachments/assets/e142fe69-471f-4a4c-a207-3a79c5e01d6b" />

再定位需要提取的字段（如id），右键点击该字段并选择 [添加为提取列]
<img width="1280" height="404" alt="image" src="https://github.com/user-attachments/assets/9643de9f-d132-4a67-928b-c0e20d80cc17" />
<img width="1280" height="211" alt="image" src="https://github.com/user-attachments/assets/70be1c44-d6d3-487e-9ba4-c361b2287bfd" />


3规则配置配置说明：
两种模式
2-1单一复合正则表达式

当一个字段需要提取多种值时、配置单一复合正则表达式，通过指定不同的捕获组编号（1, 2, 3, ...）来区分和提取不同的值。
<img width="1194" height="720" alt="image" src="https://github.com/user-attachments/assets/db85b17a-4177-4a64-92d3-aa0fcd03cd8c" />



2-3多个独立正则表达式
针对第一个目标值，编写一条只包含一个捕获组的正则。针对第二个目标值，编写另一条只包含一个捕获组的正则。以此类推，创建N个独立的规则。这种就是每条规则的意图都一目了然，看着舒服。

缺点：对于N个规则，正则引擎需要对同一字符串进行N次独立的扫描和匹配。计算开销与规则数量成正比。性能较第一种较差。
<img width="1213" height="720" alt="image" src="https://github.com/user-attachments/assets/73d7d6c9-360d-4375-8b15-6837a45ab97d" />
