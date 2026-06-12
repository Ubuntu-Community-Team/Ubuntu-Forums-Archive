---
title: "problem with c++ (with emacs editor)"
date: 2011-09-13
forum: General Help
---

### Post by nebula12 on 2011-09-13
i'm trying to make my first program, writing this:


[B]#include <iostream.h>


 int main();
 {
 cout <<"Hello World!\n";
     return 0;
 }[/B]


and in terminal it says: **iostream.h: No such file or directory**

so, i change it, as i've read on this forum:

 **#include <iostream>**  (i erased .h)

and in terminal it says:
**expected unqualified-id before ‘{’ token**


what can i do about it??
ps. i'm a total beginner with computing!!

---

### Post by TeoBigusGeekus on 2011-09-13
It has to be either
[PHP]#include <iostream>
 int main();
 {
 using namespace std;
 cout <<"Hello World!\n";
 return 0;
 }[/PHP]
or
[PHP]#include <iostream>
 int main();
 {
 std::cout <<"Hello World!\n";
 return 0;
 }[/PHP]

---

### Post by nebula12 on 2011-09-13
thanksss!

---

### Post by TeoBigusGeekus on 2011-09-13
You're welcome and don't forget to mark the thread as solved.

---

