---
title: "dirent.h header file error"
date: 2009-09-30
forum: General Help
---

### Post by hunvilr on 2009-09-30
Hi,
I am writing a C++ program in Ubuntu Linux for the first time and using the header file for directories dirent.h. 

1) i am getting an error. do i have to install the header library?
2) i just got the G++ compiler installed. do i have to install anything else?

Please tell me the command also to install it.

thanks

---

### Post by taseedorf on 2009-09-30
what is the error you're getting?  are you including the header in your code?
<include dirent.h>

---

### Post by ukblacknight on 2009-09-30
> **taseedorf said:**
> what is the error you're getting?  are you including the header in your code?
<include dirent.h>

Shouldn't it be:
```
#include <dirent.h>
```

?

---

### Post by ukblacknight on 2009-09-30
What is the output of the error?

---

### Post by Yellow Pasque on 2009-09-30
You do have the build-essential and libc6-dev package(s) installed, correct?

---

### Post by hunvilr on 2009-10-01
> **Temüjin said:**
> You do have the build-essential and libc6-dev package(s) installed, correct?
i have included the header file #include<dirent.h>

i installed the g++ package not the build -essential package.
do i have to install the build essential package?

---

### Post by hunvilr on 2009-10-01
I installed the build essential package as well.
the error i am getting is this
assign1.cpp:2:17: error: dirent: No such file or directory
where assign1.cpp is the filename

---

