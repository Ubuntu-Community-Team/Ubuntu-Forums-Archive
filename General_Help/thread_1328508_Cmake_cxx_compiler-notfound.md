---
title: "Cmake_cxx_compiler-notfound"
date: 2009-11-16
forum: General Help
---

### Post by creatxr on 2009-11-16
ubuntu 9.10 ----- "CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found. Please set CMAKE_CXX_COMPILER to a valid compiler path or name." ----- what's it need? I found that there is "gcc" in "/usr/bin"

---

### Post by Giblet5 on 2009-11-16
If you got that error and needed to ask what it means, then solving that error is probably going to lead you to a few dozen more.

The cmake script you're using wants a C++ compiler.

If you haven't already, install the build-essential package.

When it complains about something new, try and figure out what package(-dev) you're missing and install that. Proceed to the next error.

---

### Post by creatxr on 2009-11-17
but i 've installed g++-4.4 & libstdc++6 & libstdc++6-4.4-dev

---

### Post by Giblet5 on 2009-11-17
In the directory where you're runnimng cmake, is there a script called "configure"?

If so, try executing ```
./configure --prefix=/usr
```

---

### Post by sajidafzal91 on 2011-09-06
yes this command is not working i have installed g++ by using apt-get install g++ i also make install cmake by using apt-get install cmake actually i want to configure mysql connectors/c to connect mysql database in c. i am using gcc compiler plz help me

---

### Post by sajidafzal91 on 2011-09-06
how to ckeck that what package is missing???

---

