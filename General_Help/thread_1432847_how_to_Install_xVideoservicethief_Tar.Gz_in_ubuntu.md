---
title: "how to Install xVideoservicethief Tar.Gz in ubuntu 9.10"
date: 2010-03-18
forum: General Help
---

### Post by piyushchandrakar on 2010-03-18
[FONT="Tahoma"][/FONT]i am running ubuntu 9.10 i need to install the xVideo service thief into my system which is in tar.gz file. please tell me how to install these softwares that comes in Tar.gz format.

---

### Post by beastrace91 on 2010-03-18
Typically installing software from source (tar.gz) is done with the following three commands:

```
./configure
make
make install
```

All run in terminal while you are in the directory of the extracted contents. Does the archive contain a "README" or "install directions" file? If it does take a look in either of these files for how to install it.

~Jeff

---

### Post by jcp2mill on 2010-03-18
you can download version 2.3.5 of this from getdeb.net

---

### Post by pakki on 2010-04-11
usama@usama-desktop:~$ cd Desktop
usama@usama-desktop:~/Desktop$ cd xVST_2_4-linux-dynamic
usama@usama-desktop:~/Desktop/xVST_2_4-linux-dynamic$ ./configure
bash: ./configure: No such file or directory
usama@usama-desktop:~/Desktop/xVST_2_4-linux-dynamic$ ./install.sh

-------------------
xVST Install script
-------------------

xVST will be installed to: '/home/usama/xVideoServiceThief'

Installing xVST
Installing xVST files (xUpdater, plugins, languages...)
Previous version of xVST detected... removing old files...

-------------------------------------------------
xVST has been installed on your system! Enjoy it!
Visit us at: wwww.xviservicethief.sourceforge.net
-------------------------------------------------

usama@usama-desktop:~/Desktop/xVST_2_4-linux-dynamic$ 


u see ./configure method isnt meant here
**[COLOR="Blue"]Though i hav installed successfully the application but i dont knw how to run it!![/COLOR]**

in my home folder thr exists xVideoServiceThief folder containing single xvst file but i dont knw how to run it

---

### Post by 3rdalbum on 2010-04-11
Read the instructions, or if there aren't any, drag the program to the terminal.

---

