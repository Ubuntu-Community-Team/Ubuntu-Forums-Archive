---
title: "iostream.h help in c++ programs"
date: 2011-01-05
forum: General Help
---

### Post by COKEDUDE on 2011-01-05
Which package or library do we need to use iostream.h in c++ programs? I tried to compile a c++ here with no luck. The first fraction one.

[http://www.cplusplus.com/src/](http://www.cplusplus.com/src/)
[http://www.cplusplus.com/files/fraction.zip](http://www.cplusplus.com/files/fraction.zip)

```
~ $ g++ -Wall /home/mint/Downloads/Fraction.cpp
/home/mint/Downloads/Fraction.cpp:8: fatal error: iostream.h: No such file or directory
compilation terminated.
```

I have the g++, g++-4.3, g++-4.4, and g++-4.5
[http://packages.ubuntu.com/search?keywords=g%2B%2B&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=g%2B%2B&searchon=names&suite=maverick&section=all)

---

### Post by TeoBigusGeekus on 2011-01-05
Open the source file with a text editor and change the
```
#include <iostream.h>
```
to 
```
#include <iostream>
```

---

### Post by COKEDUDE on 2011-01-05
> **TeoBigusGeekus said:**
> Open the source file with a text editor and change the
```
#include <iostream.h>
```
to 
```
#include <iostream>
```

Thank you. Its annoying that you have to include the .h with c programs, but not with c++ programs. 

[http://en.wikipedia.org/wiki/C_standard_library](http://en.wikipedia.org/wiki/C_standard_library)
[http://en.wikipedia.org/wiki/C%2B%2B_Standard_Library](http://en.wikipedia.org/wiki/C%2B%2B_Standard_Library)

---

### Post by saurabhmt on 2012-08-14
> **COKEDUDE said:**
> Thank you. Its annoying that you have to include the .h with c programs, but not with c++ programs. 

[http://en.wikipedia.org/wiki/C_standard_library](http://en.wikipedia.org/wiki/C_standard_library)
[http://en.wikipedia.org/wiki/C%2B%2B_Standard_Library](http://en.wikipedia.org/wiki/C%2B%2B_Standard_Library)
I have a program in cpp named "CODE.CPP". I made it on windows platform. Now I would like to run it on ubuntu 11.04. I have used the command:
gcc CODE.CPP -o CODE

the following error is shown.........

saurabhkumar@ubuntu:~$ g++ CODE.CPP -o code
CODE.CPP: In member function &#8216;void node::disp()&#8217;:
CODE.CPP:15: error: &#8216;cout&#8217; was not declared in this scope
CODE.CPP: In member function &#8216;void node::insert()&#8217;:
CODE.CPP:20: error: &#8216;cout&#8217; was not declared in this scope
CODE.CPP:21: error: &#8216;cin&#8217; was not declared in this scope
CODE.CPP: In member function &#8216;float node::distcal(node)&#8217;:
CODE.CPP:67: error: &#8216;abs&#8217; was not declared in this scope
CODE.CPP: In member function &#8216;node node::operator=(node)&#8217;:
CODE.CPP:78: error: name lookup of &#8216;i&#8217; changed for ISO &#8216;for&#8217; scoping
CODE.CPP:78: note: (if you use &#8216;-fpermissive&#8217; G++ will accept your code)
CODE.CPP: In function &#8216;int dist(node, node)&#8217;:
CODE.CPP:106: error: &#8216;abs&#8217; was not declared in this scope
CODE.CPP: At global scope:
CODE.CPP:111: error: &#8216;::main&#8217; must return &#8216;int&#8217;
CODE.CPP: In function &#8216;int main()&#8217;:
CODE.CPP:122: error: &#8216;clrscr&#8217; was not declared in this scope
CODE.CPP:131: error: &#8216;cout&#8217; was not declared in this scope
CODE.CPP:131: error: name lookup of &#8216;m&#8217; changed for ISO &#8216;for&#8217; scoping
CODE.CPP:145: error: name lookup of &#8216;i&#8217; changed for ISO &#8216;for&#8217; scoping
CODE.CPP:194: error: &#8216;abs&#8217; was not declared in this scope
CODE.CPP:251: error: &#8216;abs&#8217; was not declared in this scope
CODE.CPP:280: error: name lookup of &#8216;k&#8217; changed for ISO &#8216;for&#8217; scoping
CODE.CPP:289: error: &#8216;abs&#8217; was not declared in this scope
CODE.CPP:309: error: name lookup of &#8216;j&#8217; changed for ISO &#8216;for&#8217; scoping

The program is running successfully in turbo C++ compiler. Can anyone please resolve this problem.
Thank you

---

### Post by wildmanne39 on 2012-08-14
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful

---

