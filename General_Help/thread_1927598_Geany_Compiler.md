---
title: "Geany Compiler"
date: 2012-02-18
forum: General Help
---

### Post by brain7734 on 2012-02-18
Greetings! I just installed Geany and I'm reading "Teach Yourself C++ for Linux." I was trying to do the initial program 'Hello World.' Geany says there is an error with *cout *when I enter the source code*. *I know this is output, but I can't figure out what the problem is. Can anyone fill me in?

---

### Post by bathacid on 2012-02-18
do you have "using namespace std;" before main? if not that may be your problem

---

### Post by 3Miro on 2012-02-18
Hi,

Geany is not a compiler, it is an editor for files. The Linux C/C++ compiler is GCC. You can install it along with all the basic tools by running:
```
sudo apt-get install build-essential
```

A basic Hello World program would look like this:
```
#include <iostream>
using namespace std;
int main( int argc, char **argv){
  cout << "Hello Cruel World!" << endl;
  return 0;
};
```

If you put the code into a file called "HelloWorld.cpp", then you can compile and run the program with:
```
g++ HelloWorld.cpp -o HelloWorld
./HelloWorld
```

This should work. I cannot say what error you are getting without looking at the code of your program.

---

### Post by brain7734 on 2012-02-18
Thanks 3Miro!!

---

### Post by raja.genupula on 2012-02-18
thats good news  :D , please don't forget marking the thread as solved from thread tools . :D

---

