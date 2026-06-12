---
title: "Install aircrack-ng from source"
date: 2012-03-05
forum: General Help
---

### Post by spiky001 on 2012-03-05
Hi  I,m trying to install aircrack from source on a lfs build system, I,m on the aircrack page [here]("http://www.aircrack-ng.org/doku.php?id=install_aircrack#installing_pre-compiled_binaries") 
I have installed the dependecies as required I,m stuck at this part as to what to do,
If some one could help.

**OS X**

    Change CFLAGS in src/Makefile to point to the macpports install of sqlite3 before compiling. Change the following line:  
 CFLAGS += -Iinclude    to  
 CFLAGS += -Iinclude -arch i386 -I/opt/local/include -L/opt/local/lib  
  ****

Or is this part for Mac

---

### Post by Ms. Daisy on 2012-03-08
aircrack is not supported on this forum.

I don't know if the LFS website would support it in their help, but perhaps you'll do better there.

---

