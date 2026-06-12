---
title: "C++ question"
date: 2006-06-15
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-15
I have written my first program with kdevelop. I am new to this and I am wondering how to make my code into an actual file? Maybe a .exe or .deb ?

Any help would be much appreciated.

---

### Post by kevlarman on 2006-06-15
to make a .exe, you would need windows, or at the very least wine; making a .deb is probably pointless and definately over your head if you're just writing your first program; so i'm going to assume you meant that you just want to compile your code. if you created a project in kdevelop, just find 'build' in the menus (there's probably a button too, i haven't used kdevelop); if you didn't, then you probably should, but if you absolutely must compile it without a kdevelop project (in which case why would you use kdevelop anyway), you can just type g++ yoursourcefilehere.cpp

---

### Post by eth on 2006-06-15
assuming kevlarman being right, more precisely:

**g++ -o filename filename.cpp classfile1.cpp classfile2.cpp (. . .) classfile1.h classfile2.h (. . .)**

then you just 

**./filename**

and your program will be running...well, aside from errors and bugs! ;)

---

