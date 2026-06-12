---
title: "C++ will not compile."
date: 2010-08-12
forum: General Help
---

### Post by Decae on 2010-08-12
I have wanted to program in C++ for some time, but every time I use any sort of IDE (CodeBlocks, Anjuta, Eclipse) they will never compile and run properly. For Code::Blocks, it had the following error:

```
sh: /home/decae/C++/Test/Untitled1: Permission denied
```This happens with any code I put in, such as this:

```
#include <iostream>
using namespace std;
int main(){
cout<<"Hello\n";
system("PAUSE");
}
```Am I doing something wrong? Do I not have the library or what? By the way, I have only had Ubuntu for a couple days so I'm still a bit confused on how to work everything. Any help will be appreciated. :D

---

### Post by GregBrannon on 2010-08-12
Confirm that you have the gcc (gnu compiler collection) installed.  If not, install them with

```
sudo apt-get install build-essentials
```

Then make sure your source files are being saved by the IDEs with an appropriate name.  For the source you showed, hello.cpp might be appropriate, but the .cpp extension is important to have on whatever name you give the file.

Then try the IDE command to compile/build/run and let us know what happens.

For quicker responses, consider posting your future programming threads in the Programming Talk area.

---

### Post by Decae on 2010-08-12
When I put the code into the terminal, here's what I got:

```
~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
```

So, where could I find this package?

---

### Post by Nytram on 2010-08-12
I believe that *build-essentials* was for older versions of Ubuntu and is now deprecated. You should already have *gcc* on your system if you're using 10.04 - try typing **gcc** into a terminal.

I don't know a lot about using C++ but I would start with trying to compile a program in the terminal i.e. without using an IDE. That way you can see what errors come up and look for solutions.

The usage is:

**gcc inputfile.cpp**

Also as GregBrannon mentions there's a Programming section on these forums where you can get more help:

[http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by Decae on 2010-08-12
When I type gcc into the terminal, it says "gcc: no input files". I think that's it... How would I fix this? :confused:

---

### Post by krishnandu.sarkar on 2010-08-12
g++ -o filename.c /filename

---

