### Python快速入门

**如果你缺少编程基础，或者Python是你学习的第一门编程语言请先移步[这里](https://mp.weixin.qq.com/s/I0iT3SLaKOvdtzWojt0Xag)阅读电子书。**

Python是一种高级的、动态类型的多范型编程语言。Python代码通常被认为是伪代码，因为它允许您在非常可读的几行代码中表达非常强大的思想。作为一个例子，下面是Python中经典的快速排序算法的实现:

```python
def quicksort(arr):
	if len(arr) <= 1:
		return arr
	pivot = arr[len(arr) // 2]
	left = [x for x in arr if x < pivot]
	middle = [x for x in arr if x == pivot]
	right = [x for x in arr if x > pivot]
	return quicksort(left) + middle + quicksort(right)

print(quicksort([3,6,8,10,1,2,1]))
# Prints "[1, 1, 2, 3, 6, 8, 10]"
```

##### Python版本

目前有两种不同的Python版本，分别是2.7和3.5。Python 3.0引入了许多对语言不兼容的更改，因此为2.7编写的代码可能不能在3.5下工作。
 您可以通过运行Python-version来检查命令行中的Python版本。

##### 基本数据类型

与大多数语言一样，Python有许多基本类型，包括整数、浮点数、布尔值和字符串。这些数据类型的使用方式与其他编程语言很相似。
 数字:整数和浮点数可以从其他语言中得到:

```python
x = 3
print(type(x)) # Prints "<class 'int'>"
print(x)       # Prints "3"
print(x + 1)   # Addition; prints "4"
print(x - 1)   # Subtraction; prints "2"
print(x * 2)   # Multiplication; prints "6"
print(x ** 2)  # Exponentiation; prints "9"
x += 1
print(x)  # Prints "4"
x *= 2
print(x)  # Prints "8"
y = 2.5
print(type(y)) # Prints "<class 'float'>"
print(y, y + 1, y * 2, y ** 2) # Prints "2.5 3.5 5.0 6.25"
```

注意，与许多语言不同的是，Python不支持增量(x++)或递减(x--)操作符。
 Python也有用于复数的内置类型;您可以在文档中找到所有的细节。

**布尔值**:Python实现了布尔逻辑的所有常用操作符，但使用的是英语单词而不是符号(&&等等):

```python
t = True
f = False
print(type(t)) # Prints "<class 'bool'>"
print(t and f) # Logical AND; prints "False"
print(t or f)  # Logical OR; prints "True"
print(not t)   # Logical NOT; prints "False"
print(t != f)  # Logical XOR; prints "True"
```

**字符串**:Python对字符串有很大的支持:

```python
hello = 'hello'    # String literals can use single quotes
world = "world"    # or double quotes; it does not matter.
print(hello)       # Prints "hello"
print(len(hello))  # String length; prints "5"
hw = hello + ' ' + world  # String concatenation
print(hw)  # prints "hello world"
hw12 = '%s %s %d' % (hello, world, 12)  # sprintf style string formatting
print(hw12)  # prints "hello world 12"
```

String对象有很多有用的方法;例如:

```python
s = "hello"
print(s.capitalize())  # Capitalize a string; prints "Hello"
print(s.upper())       # Convert a string to uppercase; prints "HELLO"
print(s.rjust(7))      # Right-justify a string, padding with spaces; prints "  hello"
print(s.center(7))     # Center a string, padding with spaces; prints " hello "
print(s.replace('l', '(ell)'))  # Replace all instances of one substring with another;
                                # prints "he(ell)(ell)o"
print('  world '.strip())  # Strip leading and trailing whitespace; prints "world"
```

##### 容器

Python包括几个内置的容器类型:列表、字典、集合和元组。

**列表**
 列表是Python的一个数组，但是可以调整，并且可以包含不同类型的元素:

```python
xs = [3, 1, 2]    # Create a list
print(xs, xs[2])  # Prints "[3, 1, 2] 2"
print(xs[-1])     # Negative indices count from the end of the list; prints "2"
xs[2] = 'foo'     # Lists can contain elements of different types
print(xs)         # Prints "[3, 1, 'foo']"
xs.append('bar')  # Add a new element to the end of the list
print(xs)         # Prints "[3, 1, 'foo', 'bar']"
x = xs.pop()      # Remove and return the last element of the list
print(x, xs)      # Prints "bar [3, 1, 'foo']"
```

切片(Slicing):除了每次访问列表元素一次，Python还提供了访问子列表的简明语法;这就是所谓的切片:

```python
nums = list(range(5))     # range is a built-in function that creates a list of integers
print(nums)               # Prints "[0, 1, 2, 3, 4]"
print(nums[2:4])          # Get a slice from index 2 to 4 (exclusive); prints "[2, 3]"
print(nums[2:])           # Get a slice from index 2 to the end; prints "[2, 3, 4]"
print(nums[:2])           # Get a slice from the start to index 2 (exclusive); prints "[0, 1]"
print(nums[:])            # Get a slice of the whole list; prints "[0, 1, 2, 3, 4]"
print(nums[:-1])          # Slice indices can be negative; prints "[0, 1, 2, 3]"
nums[2:4] = [8, 9]        # Assign a new sublist to a slice
print(nums)               # Prints "[0, 1, 8, 9, 4]"
```

循环:您可以对列表的元素进行循环/遍历:

```python
animals = ['cat', 'dog', 'monkey']
for animal in animals:
	print(animal)
# Prints "cat", "dog", "monkey", each on its own line.
```

如果您想要访问循环体中的每个元素的索引，请使用内置的枚举(enumerate)函数:

```python
animals = ['cat', 'dog', 'monkey']
for idx, animal in enumerate(animals):
	print('#%d: %s' % (idx + 1, animal))
# Prints "#1: cat", "#2: dog", "#3: monkey", each on its own line
```

列表理解:在编程时，我们经常需要将一种类型的数据转换为另一种类型。作为一个简单的例子，考虑下面的代码计算平方数:

```python
nums = [0, 1, 2, 3, 4]
squares = []
for x in nums:
	squares.append(x ** 2)
print(squares)   # Prints [0, 1, 4, 9, 16]
```

您可以使用列表理解来简化这段代码:

```python
nums = [0, 1, 2, 3, 4]
squares = [x ** 2 for x in nums]
print(squares)   # Prints [0, 1, 4, 9, 16]
```

列表理解也可以包含条件:

```python
nums = [0, 1, 2, 3, 4]
even_squares = [x ** 2 for x in nums if x % 2 == 0]
print(even_squares)  # Prints "[0, 4, 16]"
```

**字典**
 字典存储(键、值)对，类似于Java中的映射或Javascript中的对象。你可以这样使用它:

```python
d = {'cat': 'cute', 'dog': 'furry'}  # Create a new dictionary with some data
print(d['cat'])       # Get an entry from a dictionary; prints "cute"
print('cat' in d)     # Check if a dictionary has a given key; prints "True"
d['fish'] = 'wet'     # Set an entry in a dictionary
print(d['fish'])      # Prints "wet"
# print(d['monkey'])  # KeyError: 'monkey' not a key of d
print(d.get('monkey', 'N/A'))  # Get an element with a default; prints "N/A"
print(d.get('fish', 'N/A'))    # Get an element with a default; prints "wet"
del d['fish']         # Remove an element from a dictionary
print(d.get('fish', 'N/A')) # "fish" is no longer a key; prints "N/A"
```

循环:在字典中对键进行迭代是很容易的:

```python
d = {'person': 2, 'cat': 4, 'spider': 8}
for animal in d:
	legs = d[animal]
	print('A %s has %d legs' % (animal, legs))
# Prints "A person has 2 legs", "A cat has 4 legs", "A spider has 8 legs"
```

如果您想要访问键值（keys）及其对应的值，请使用items方法:

```python
d = {'person': 2, 'cat': 4, 'spider': 8}
for animal, legs in d.items():
	print('A %s has %d legs' % (animal, legs))
# Prints "A person has 2 legs", "A cat has 4 legs", "A spider has 8 legs"
```

字典的理解:这些类似于列表的理解，但是允许你轻松地构造字典。例如:

```python
nums = [0, 1, 2, 3, 4]
even_num_to_square = {x: x ** 2 for x in nums if x % 2 == 0}
print(even_num_to_square)  # Prints "{0: 0, 2: 4, 4: 16}"
```

**集合**
 集合是不同元素的无序集合。作为一个简单的例子，请考虑以下内容:

```python
animals = {'cat', 'dog'}
print('cat' in animals)   # Check if an element is in a set; prints "True"
print('fish' in animals)  # prints "False"
animals.add('fish')       # Add an element to a set
print('fish' in animals)  # Prints "True"
print(len(animals))       # Number of elements in a set; prints "3"
animals.add('cat')        # Adding an element that is already in the set does nothing
print(len(animals))       # Prints "3"
animals.remove('cat')     # Remove an element from a set
print(len(animals))       # Prints "2"
```

循环:在一个集合上的迭代与遍历列表的语法相同;然而，由于集合是无序的，所以您不能对您访问集合元素的顺序作出假设:

```python
animals = {'cat', 'dog', 'fish'}
for idx, animal in enumerate(animals):
	print('#%d: %s' % (idx + 1, animal))
# Prints "#1: fish", "#2: dog", "#3: cat"
```

集合:像列表和字典一样，我们可以用集合的理解来轻松地构建集合:

```cpp
from math import sqrt
nums = {int(sqrt(x)) for x in range(30)}
print(nums)  # Prints "{0, 1, 2, 3, 4, 5}"
```

**元组**
 tuple是一个(不可变的)有序的值列表。元组在许多方面与列表相似;最重要的区别之一是，元组可以用作字典中的键，也可以作为集合的元素，而列表则不能。这里有一个简单的例子:

```python
d = {(x, x + 1): x for x in range(10)}  # Create a dictionary with tuple keys
t = (5, 6)        # Create a tuple
print(type(t))    # Prints "<class 'tuple'>"
print(d[t])       # Prints "5"
print(d[(1, 2)])  # Prints "1"
```

方法/函数
 Python函数是使用def关键字定义的。例如:

```kotlin
def sign(x):
	if x > 0:
		return 'positive'
	elif x < 0:
		return 'negative'
	else:
		return 'zero'

for x in [-1, 0, 1]:
	print(sign(x))
# Prints "negative", "zero", "positive"
```

我们通常会定义一些函数来选择可选的关键字参数，比如:

```python
def hello(name, loud=False):
	if loud:
		print('HELLO, %s!' % name.upper())
	else:
		print('Hello, %s' % name)

hello('Bob') # Prints "Hello, Bob"
hello('Fred', loud=True)  # Prints "HELLO, FRED!"
```

**类**
 在Python中定义类的语法很简单:

```python
class Greeter(object):

	# Constructor
	def __init__(self, name):
		self.name = name  # Create an instance variable

	# Instance method
	def greet(self, loud=False):
		if loud:
			print('HELLO, %s!' % self.name.upper())
		else:
			print('Hello, %s' % self.name)
            
	@property
	def words(self):
		return 'Hello'

g = Greeter('Fred')  # Construct an instance of the Greeter class
g.greet()            # Call an instance method; prints "Hello, Fred"
g.greet(loud=True)   # Call an instance method; prints "HELLO, FRED!"
print(g.words)		 # @property will change function as a property
```

**Turtle作图**

turtle类用于画图：

```python
import turtle

t = turtle.Turtle()

for c in ['red', 'green', 'yellow', 'blue']:
    t.color(c)
    t.forward(75)
    t.left(90)
```

**Lambda**

Lambda表达式是简单的函数：

```python
r = 10
result = lambda r : 3.14 * r ** 2
print(result(r))
```

**断言与异常处理**

```python
if __name__ == '__main__':
    apple = 4
    children = 5
    try:
        assert apple >= children, "苹果不够"
    except AssertionError as e:
        print(e)
```

#### Python3 正则表达式

正则表达式是一个特殊的字符序列，它能帮助你方便的检查一个字符串是否与某种模式匹配。

**re.match函数**

re.match 尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，match()就返回none。


re.match(pattern, string, flags=0)


函数参数说明：

| 参数    | 描述                                                         |
| :------ | :----------------------------------------------------------- |
| pattern | 匹配的正则表达式                                             |
| string  | 要匹配的字符串。                                             |
| flags   | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。 |

匹配成功re.match方法返回一个匹配的对象，否则返回None。

我们可以使用group(num) 或 groups() 匹配对象函数来获取匹配表达式。

| 匹配对象方法 | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| group(num=0) | 匹配的整个表达式的字符串，group() 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。 |
| groups()     | 返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。     |

```python
import re  
line = "Cats are smarter than dogs" # .* 表示任意匹配除换行符（\n、\r）之外的任何单个或多个字符 # (.*?) 表示"非贪婪"模式，只保存第一个匹配到的子串 
matchObj = re.match( r'(.*) are (.*?) .*', line, re.M|re.I)  
if matchObj:   
    print ("matchObj.group() : ", matchObj.group())   
    print ("matchObj.group(1) : ", matchObj.group(1))   
    print ("matchObj.group(2) : ", matchObj.group(2)) 
else:   
    print ("No match!!")
```

以上实例执行结果如下：

matchObj.group() :  Cats are smarter than dogs
matchObj.group(1) :  Cats
matchObj.group(2) :  smarter

**re.search方法**

re.search 扫描整个字符串并返回第一个成功的匹配。

函数语法：

re.search(pattern, string, flags=0)

函数参数说明：

| 参数    | 描述                                                         |
| :------ | :----------------------------------------------------------- |
| pattern | 匹配的正则表达式                                             |
| string  | 要匹配的字符串。                                             |
| flags   | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。 |

匹配成功re.search方法返回一个匹配的对象，否则返回None。

我们可以使用group(num) 或 groups() 匹配对象函数来获取匹配表达式。

| 匹配对象方法 | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| group(num=0) | 匹配的整个表达式的字符串，group() 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。 |
| groups()     | 返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。     |

```python
import re  
line = "Cats are smarter than dogs"  
searchObj = re.search( r'(.*) are (.*?) .*', line, re.M|re.I)  
if searchObj:   
	print ("searchObj.group() : ", searchObj.group())   
	print ("searchObj.group(1) : ", searchObj.group(1))   
	print ("searchObj.group(2) : ", searchObj.group(2)) 
else:   
	print ("Nothing found!!")
```

以上实例执行结果如下：

searchObj.group() :  Cats are smarter than dogs
searchObj.group(1) :  Cats
searchObj.group(2) :  smarter

**re.match与re.search的区别**

re.match 只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回 None，而 re.search 匹配整个字符串，直到找到一个匹配。

```python
import re  
line = "Cats are smarter than dogs"  
matchObj = re.match( r'dogs', line, re.M|re.I) 
if matchObj:   
	print ("match --> matchObj.group() : ", matchObj.group())
else:   
	print ("No match!!")  
	matchObj = re.search( r'dogs', line, re.M|re.I) 
if matchObj:   
	print ("search --> matchObj.group() : ", matchObj.group()) 
else:   
	print ("No match!!")
```

以上实例运行结果如下：


No match!!
search --> matchObj.group() :  dogs

**检索和替换**

Python 的re模块提供了re.sub用于替换字符串中的匹配项。

语法：

re.sub(pattern, repl, string, count=0, flags=0)

参数：

- pattern : 正则中的模式字符串。
- repl : 替换的字符串，也可为一个函数。
- string : 要被查找替换的原始字符串。
- count : 模式匹配后替换的最大次数，默认 0 表示替换所有的匹配。
- flags : 编译时用的匹配模式，数字形式。

前三个为必选参数，后两个为可选参数。

**compile 函数**

compile 函数用于编译正则表达式，生成一个正则表达式（ Pattern ）对象，供 match() 和 search() 这两个函数使用。

语法格式为：

re.compile(pattern[, flags])

参数：

- pattern : 一个字符串形式的正则表达式
- flags 可选，表示匹配模式，比如忽略大小写，多行模式等，具体参数为：
- - re.I 忽略大小写

  - re.L 表示特殊字符集 \w, \W, \b, \B, \s, \S 依赖于当前环境
  - re.M 多行模式
  - re.S 即为' . '并且包括换行符在内的任意字符（' . '不包括换行符）
  - re.U 表示特殊字符集 \w, \W, \b, \B, \d, \D, \s, \S 依赖于 Unicode 字符属性数据库
  - re.X 为了增加可读性，忽略空格和' # '后面的注释

在上面，当匹配成功时返回一个 Match 对象，其中：

- `group([group1, …])` 方法用于获得一个或多个分组匹配的字符串，当要获得整个匹配的子串时，可直接使用 `group()` 或 `group(0)`；
- `start([group])` 方法用于获取分组匹配的子串在整个字符串中的起始位置（子串第一个字符的索引），参数默认值为 0；
- `end([group])` 方法用于获取分组匹配的子串在整个字符串中的结束位置（子串最后一个字符的索引+1），参数默认值为 0；
- `span([group])` 方法返回 `(start(group), end(group))`。

**findall**

在字符串中找到正则表达式所匹配的所有子串，并返回一个列表，如果没有找到匹配的，则返回空列表。

**注意：** match 和 search 是匹配一次 findall 匹配所有。

语法格式为：

re.findall(pattern, string, flags=0)
或
pattern.findall(string[, pos[, endpos]])

参数：

- **pattern** 匹配模式。
- **string** 待匹配的字符串。
- **pos** 可选参数，指定字符串的起始位置，默认为 0。
- **endpos** 可选参数，指定字符串的结束位置，默认为字符串的长度。

查找字符串中的所有数字：

```python
import re  
result1 = re.findall(r'\d+','runoob 123 google 456')  
pattern = re.compile(r'\d+')   # 查找数字 
result2 = pattern.findall('run88oob123google456', 0, 10)  
print(result1) 
print(result2) 
```

输出结果：

['123', '456']
['88', '12']

**正则表达式实例**

字符匹配

| 实例   | 描述           |
| :----- | :------------- |
| python | 匹配 "python". |

字符类

| 实例        | 描述                              |
| :---------- | :-------------------------------- |
| [Pp]ython   | 匹配 "Python" 或 "python"         |
| rub[ye]     | 匹配 "ruby" 或 "rube"             |
| [aeiou]     | 匹配中括号内的任意一个字母        |
| [0-9]       | 匹配任何数字。类似于 [0123456789] |
| [a-z]       | 匹配任何小写字母                  |
| [A-Z]       | 匹配任何大写字母                  |
| [a-zA-Z0-9] | 匹配任何字母及数字                |
| [^aeiou]    | 除了aeiou字母以外的所有字符       |
| [^0-9]      | 匹配除了数字外的字符              |

特殊字符类

| 实例 | 描述                                                         |
| :--- | :----------------------------------------------------------- |
| .    | 匹配除 "\n" 之外的任何单个字符。要匹配包括 '\n' 在内的任何字符，请使用象 '[.\n]' 的模式。 |
| \d   | 匹配一个数字字符。等价于 [0-9]。                             |
| \D   | 匹配一个非数字字符。等价于 [^0-9]。                          |
| \s   | 匹配任何空白字符，包括空格、制表符、换页符等等。等价于 [ \f\n\r\t\v]。 |
| \S   | 匹配任何非空白字符。等价于 [^ \f\n\r\t\v]。                  |
| \w   | 匹配包括下划线的任何单词字符。等价于'[A-Za-z0-9_]'。         |
| \W   | 匹配任何非单词字符。等价于 '[^A-Za-z0-9_]'。                 |

#####更多有关Python3的详细资料可以移步[这里](https://mp.weixin.qq.com/s/I0iT3SLaKOvdtzWojt0Xag)。

