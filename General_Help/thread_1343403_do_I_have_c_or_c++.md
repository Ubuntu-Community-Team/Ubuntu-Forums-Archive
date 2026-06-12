---
title: "do I have c or c++?"
date: 2009-12-01
forum: General Help
---

### Post by suri.mahendra on 2009-12-01
I am going back to school for database admin.  I am required to take c++ and oop c++.  I have downloaded cpp 4.2 along with all the libs and compilers to write programs.  However I've noticed some differences in code between what I do and what the text says.  The text is based on visual c++ 6.0.

The text requires C++ code to start as thus:
#include <iostream.h>
int main ()

I get compile-time errors unless I start my code as such:
#include <iostream.h>
using namespace std;
int main()

Do I have c++ or do I have c?
Are these differences due the fact I have c/c++ version 4.x and the text is using visual c++ 6.x?

How do I rectify this?

cheers

---

### Post by pbrane on 2009-12-01
I think the problem is that the visual C++ code is doing something like
```

cout << text << endl;

```

if you specify **using namespace std** the C++ compiler finds the cout function but if you don't specify **using namespace std** then you need to change the code to 
```

std::cout << text << std::endl;

```

where you are specifying the actual namespace per function call. Also it is not standard C++ to use **#include <iostream.h>** anymore, the syntax **#include <iostream>** is used instead. Microsoft Visual C++ is not always standards compliant, it will accept some syntax that GNU C++ may not.

This may be of some help:
[http://www.cppreference.com/wiki/]("http://www.cppreference.com/wiki/")

---

