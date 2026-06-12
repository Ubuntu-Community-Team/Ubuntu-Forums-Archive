---
title: "c++ system(&quot;clear&quot;) can not be compiled"
date: 2009-10-12
forum: General Help
---

### Post by nugroho.redbuff on 2009-10-12
Hi every buddy!

I wrote program like this bellow:
#include<iostream>
#include<string>
using namespace std;
//variable definiton
   float r, t;
   float vol, luasl, luasd, luast;

//input section
void masukan(){
system("clear");
bla..bla...bla..
}

ect

when i compile the program, the message tells me that "system" is not declared. 
Please help me to solve this and I can clear the screen using cpp.
Thanks

Nugroho.redbuff:P

---

### Post by Giblet5 on 2009-10-12
> **nugroho.redbuff said:**
> Hi every buddy!

I wrote program like this bellow:
#include<iostream>
#include<string>

**#include <stdlib.h>**

using namespace std;
//variable definiton
   float r, t;
   float vol, luasl, luasd, luast;

//input section
void masukan(){
system("clear");
bla..bla...bla..
}

ect

when i compile the program, the message tells me that "system" is not declared. 
Please help me to solve this and I can clear the screen using cpp.
Thanks

Nugroho.redbuff:P

That'll fix it.

---

### Post by kjohri on 2009-10-13
#include <stdlib.h>

---

