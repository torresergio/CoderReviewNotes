# C++ STL 和 常用库

## 1. STL

### 6.1 vector

头文件：`#include <vector>`

vector 是一个泛型动态数组，相当于 java 的 ArrayList。与 java 不同的是，泛型可以是内建的 int ，double 等类型。

**属性和类型介绍**

- size —— 数组当前大小，指存的元素个数
- capacity —— 当前数组的容量，超过这个容量就要扩容
- vector\<T\>::iterator —— 迭代器类型

**构造方法**

- vector(void) —— 默认构造，size 和 capacity 都为零。
- vector(int size) —— 构造 size 个元素的数组，每个元素进行默认的初始化。
- vector(int size, T initial_value) —— 构造 size 个元素的数组，每个元素进行指定初始化。
- vector(vector\<T\> v) —— 拷贝构造
- vector(vector\<T\>::iterator begin, vector\<T\>::iterator end) —— 使用迭代器内的元素构造。
- vector 也支持数组的大括号初始化，如 `vector<int> {1,2}`

**运算符重载**

- operator[] —— 使之支持静态数组的访问方式

**成员方法**

- at(int index) ——传回索引 index 所指的数据，如果越界，抛出out_of_range。
- push_back(T value)
- pop_back()
- front() —— 传回第一个数据
- back() —— 传回最后一个数据，不检查这个数据是否存在。 
- swap(int idx1, int idx2)
- insert(int pos, T value) 
- insert(int pos, int n, T value)
- insert(int pos, vector\<T\>::iterator begin, vector\<T\>::iterator end)
- assign(int n, T value)
- assign(vector\<T\>::iterator begin, vector\<T\>::iterator end)
- begin() 
- end()
- clear() 
- size()
- max_size()
- empty() 
- resize(int size)
- reserve() —— 保留适当的容量
- rbegin() 
- rend() 

**原理**

它拥有一段连续的内存空间，并且起始地址不变，因此它能非常好的支持随即存取，即[]操作符，但由于它的内存空间是连续的，所以在中间进行插入和删除会造成内存块的拷贝，另外，当该数组后的内存空间不够时，需要重新申请一块足够大的内存并进行内存的拷贝。这些都大大影响了vector的效率。

### 6.2 list

头文件：`#include <list>`

C++ 中的双向链表，类似于 java 的 LinkedList。

**属性和类型介绍**

- size —— 链表当前大小
- li's't\<T\>::iterator —— 迭代器类型

**构造函数**

- list()
- list(int size)
- list(int size, T initial_value)
- list(list<T\> l)
- list(list\<T\>::iterator begin, list\<T\>::iterator end)

**成员函数**

- push_front(T value)
- pop_front()
- push_back(T value)
- pop_back()
- front() —— 传回第一个数据
- back() —— 传回最后一个数据，不检查这个数据是否存在。 
- insert(list\<T\>::iterator pos, T value)
- remove(T value) ——删除所有值为value的元素
- unique() ——删除所有重复的元素
- begin() 
- end()
- size()
- clear() 
- empty() 

**原理**

list就是双向链表,元素也是在堆中存放,每个元素都是放在一块内存中,它的内存空间可以是不连续的，通过指针来进行数据的访问，这个特点使得它的随即存取变的非常没有效率，因此它没有提供[]操作符的重载。但由于链表的特点，它可以以很好的效率支持任意地方的删除和插入。

list没有空间预留习惯,所以每分配一个元素都会从内存中分配,每删除一个元素都会释放它占用的内存.

### 6.3 set

### 6.4 map

头文件：`#include <map>`

map 即 C++ 的映射表。

**属性和类型介绍**

- size —— 数组当前大小，指存的元素个数
- map \<K，V>::iterator —— 迭代器类型

**构造方法**

- map (void) —— 默认构造。
- map (map \<K，V> m) —— 拷贝构造
- map (map \<K，V>::iterator begin, map \<K，V>::iterator end) —— 使用迭代器内的元素构造。

**运算符重载**

- operator[] —— 使之支持数组的访问方式，下标为key。当下标不存在时不会保存，整形返回 0 值。

**成员方法**

- at(int index) ——传回索引 index 所指的数据，如果越界，抛出out_of_range。
- push_back(T value)
- pop_back()
- front() —— 传回第一个数据
- back() —— 传回最后一个数据，不检查这个数据是否存在。 
- swap(int idx1, int idx2)
- insert(int pos, T value) 
- insert(int pos, int n, T value)
- insert(int pos, vector\<T\>::iterator begin, vector\<T\>::iterator end)
- assign(int n, T value)
- assign(vector\<T\>::iterator begin, vector\<T\>::iterator end)
- begin() 
- end()
- clear() 
- size()
- max_size()
- empty() 
- resize(int size)
- reserve() —— 保留适当的容量
- rbegin() 
- rend() 

**原理**

c++ 的 map 和 set 都是单单用红黑树实现的。因为 map 和 set 都要求是有序集合。

无序的有 unordered_map ，使用的数组加链表。

### 6.5 deque

头文件：`#include <deque>`

双端队列。

**属性和类型介绍**

- size —— 链表当前大小
- deque\<T\>::iterator —— 迭代器类型

**构造函数**

- deque()
- deque(int size)
- deque(int size, T initial_value)
- deque(deque<T\> l)
- deque(deque\<T\>::iterator begin, deque\<T\>::iterator end)

**运算符重载**

- operator[] —— 使之支持数组的访问方式，但效率较低

**成员函数**

- at(int idx)
- push_front(T value)
- pop_front()
- push_back(T value)
- pop_back()
- front() —— 传回第一个数据
- back() —— 传回最后一个数据，不检查这个数据是否存在。 
- begin() 
- end()
- size()
- max_size()
- clear() 
- empty()

**原理**

在标准库中vector和deque提供几乎相同的接口,在结构上它们的区别主要在于这两种容器在组织内存上不一样,deque是按页或块来分配存储器的,每页包含固定数目的元素.相反vector分配一段连续的内存,vector只是在序列的尾段插入元素时才有效率,而deque的分页组织方式即使在容器的前端也可以提供常数时间的insert和erase操作,而且在体积增长方面也比vector更具有效率。

同一页或同一块的元素是相邻的，页与页之间的位置是堆内随机的。

### 6.6 stack

头文件：`#include <stack>`

栈，由 deque 装饰而来。

**属性和类型介绍**

- size —— 链表当前大小

**构造函数**

- stack()

**成员函数**

- push(T value)
- pop()
- top() —— 返回栈顶 
- size()
- clear() 
- empty()

### 6.7 queue

头文件：`#include <queue>`

普通队列，也是由 deque 装饰而来。

**属性和类型介绍**

- size —— 链表当前大小

**构造函数**

- queue()

**成员函数**

- push(T value)
- pop()
- front()
- back()
- size()
- clear() 
- empty()

### 6.8 priority_queue

头文件：`#include <queue>`

优先队列与队列的差别在于优先队列不是按照入队的顺序出队，而是按照队列中元素的优先权顺序出队 

**属性和类型介绍**

- size —— 链表当前大小

**构造函数**

- priority_queue\<type, container, compare\>() —— 
  - container 取值，默认为 vector
  - compare 的取值：greater\<int\> 从大到小（默认），less\<int\> 从小到大，需要重载大于小于运算符

**成员函数**

- push(T value)
- pop()
- top()
- size()
- clear() 
- empty()

### 6.9 pair

头文件：`#include <utility> `

pair 存储两个泛性值，pair 支持比较，首先比较第一个，第一个相同则以第二个大小关系为准。

**构造方法**

- pair()
- pair(v1, v2)
- 也可使用make_pair(v1,v2) 构造pair

**属性**

- first
- second

## 2. C 函数库

### 字符函数库 cctype

- int islower(char) —— 小写字母返回 1，否则返回 0
- int isupper(char)—— 大写字母返回 1，否则返回 0
- int isalpha(char) —— 字母返回 1，否则返回 0
- int isdigit(char)—— 数字返回 1，否则返回 0
- int isalnum(char) —— 数字或字母返回 1，否则返回 0
- int isxdigit()—— 十六进制字符返回 1，否则返回 0
- int isblank(char) —— 空格或制表符返回 1，否则返回 0
- char tolower(char)—— 大写字母则返回对于小写字母，否则返回本身
- char toupper(char)—— 小写字母则返回对于大写字母，否则返回本身