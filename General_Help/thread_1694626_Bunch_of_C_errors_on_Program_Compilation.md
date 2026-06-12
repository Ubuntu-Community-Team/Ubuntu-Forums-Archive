---
title: "Bunch of C errors on Program Compilation"
date: 2011-02-24
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2011-02-24
I'm attempting to install a small application called Asymptopia Flashcard System on Xubuntu x64. It's unsupported and virtually unknown, so I don't know many details about it aside from what I can gather from the source files. The first step in the installation directions is to type "make lib_install" as root at the command line. I get this output:

Making libasymptopia.so ... 
compiling Path.C ...
Path.C: In member function ‘void Path::listdir(char*, std::deque<char*, std::allocator<char*> >*)’:

followed by a bunch of errors like this:

Path.C:38: error: ‘strcmp’ was not declared in this scope

all for the file Path.C, all of them complaining about various header files not being declared. I have the latest version of gcc installed, so I'm very confused about what the problem is. This application is at least a few years old...maybe there's something out-of-date about the way it includes the header files?

Any ideas? Thanks.

---

### Post by Tk007LwZFJW5ej on 2011-02-24
I added #include<string.h> to Path.C

---

