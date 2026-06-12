---
title: "using a 32 bit library"
date: 2012-05-27
forum: General Help
---

### Post by EvilTesla on 2012-05-27
I currently using a networking library called ZoidCom.  It is a very usefull library that I like alot. But, it is proving to be a pain.  I am currently running Ubuntu 12.04 64 bit.    There are two versions of ZoidCom that concern me, 6.11, which is the most recent public release, and 6.10, which I am currently using. Niether of these are avaible through synaptic that I am aware of.  So when I install these libraries I just copy the headers into a zoidcom folder in /usr/include  and the dynamic libraries to /usr/lib.   However, if I use the 32 bit version of the distribution than I will get a compiler error something along the lines of wrong ELF class (ELFCLASS32). If I use the 32 bit version, and place the binaries in /use/lib32 than I get the compiler error:  &quot; skipping incompatible /usr/lib32/libzoidcom.so when searching for -lzoidcom &quot;     This is a problem becouse the newer version, 6.11, doesn't come with a 64 bit binary, or any source code. 6.10 has a 64 bit binary, but I'd like to use the newer version. And, apparently Ubuntu keeps trying to update my Zoidcom library from 6.10 to 6.11 (32 bit), so every day or two I have to reinstall the library with 6.10 64 bit.    so my question is, how do I get my 64 bit project to compile with a 32 bit binary?     thanks, EvilTesla  EDIT: why does my carefully spaced message come out like a giant wall of text?

---

