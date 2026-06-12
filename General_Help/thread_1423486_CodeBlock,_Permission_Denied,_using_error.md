---
title: "CodeBlock, Permission Denied, using: error"
date: 2010-03-06
forum: General Help
---

### Post by sqwertle on 2010-03-06
I've just recently come back to Ubuntu after a short XP stint and I decided I wanted a C++ compiler similar to Dev-CPP, CodeBlocks seems to be it. Every attempt at compiling code initially results in this error 

```
sh: /home/sqwertle/C++/Untitled1: Permission denied
Press ENTER to continue.
```After getting this I ```
chmod a+x Untitled1
```After changing the file permissions it will compile, but then I get the following compile errors:
```

/home/sqwertle/C++/Untitled1: 3: using: not found
/home/sqwertle/C++/Untitled1: 5: Syntax error: "(" unexpected

Press ENTER to continue.
```The code I'm attempting to compile is as follows: 

```
#include <iostream>

using namespace std;

int main() {
   cout << "hello world";
   getchar();
   return 0;
}
```Upon each time a change is made to the program and I attempt to compile it, it gives me the permission denied error. I would not like to change permissions every time I attempt to compile. Also, if I've made a horribly stupid, blind-sighted mistake on the source, please let me know.

---

### Post by agnes on 2010-03-06
Had the same problem. My advice: Remove codeblocks. Then install it from their [website]("http://www.codeblocks.org/downloads/5").
I did not add the wxWidgets repository as they recommend there (2.8.10 is installed by default or in the repos).

(Also, you need to "#include <stdio.h>" for the "getchar()", but that was not the problem.)

---

