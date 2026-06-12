---
title: "g++ 64-bit"
date: 2010-09-04
forum: General Help
---

### Post by Shuttleu on 2010-09-04
is there anywhere i can get amd64-mingw32msvc-g++
i have installed mingw-w64 and it has installed the other compilers, but not the g++ compiler, and i need to compile a program for 64-bit windows

---

### Post by Shuttleu on 2010-09-05
please, anyone

---

### Post by tw33 on 2010-12-26
The mingw-w64 package in the standard repositories seems to be missing the g++ compiler. Have a look at:
[https://bugs.launchpad.net/ubuntu/+source/gcc-mingw32/+bug/568028](https://bugs.launchpad.net/ubuntu/+source/gcc-mingw32/+bug/568028)
I suspect we need to be build it from source (with 64-bit support enabled).
[http://sourceforge.net/projects/mingw-w64/](http://sourceforge.net/projects/mingw-w64/)

---

### Post by Spyderkid on 2010-12-26
If you want the G++ compiler install it by running...

```

sudo apt-get install build-essential

```




Then to save a file with your C++ code in and save it with .cpp on the end and run this to compile it (*input* being the file name and *output* being the files name afterwards)

```
g++ *input*.cpp -o *output*.cpp
```

---

### Post by cgroza on 2010-12-26
You want to compile a program for windows from ubuntu? I think this is only possible with a cross compiler...

---

