---
title: "How do you install application from source code?"
date: 2011-05-01
forum: General Help
---

### Post by TheNewbieGeek on 2011-05-01
Hi guys,

How do you install a application from source code? Thanks for the replies.

---

### Post by drpjkurian on 2011-05-01
The source code has to be recompiled and then it has to be installed..

---

### Post by lisati on 2011-05-01
Have a look for a "readme" file in the archive you download.

---

### Post by TheHimself on 2011-05-01
It depends. Professionally prepared source code usually have makefiles which make it easy to compile the code. Look if you can find a file with the name "install.sh" or just "install".

---

### Post by zander1013 on 2011-05-01
> **TheNewbieGeek said:**
> Hi guys,

How do you install a application from source code? Thanks for the replies.

hi,

i will assume that you already have gcc installed correctly. you must use gcc to do this with best results.

i have not done it in a while because the package manager is pretty good these days but the basic process used to be this...

1. download the tar file and move it to the directory where you want to have it.

2. decompress it with gzip if its compressed...
gzip -d <filename>
2a. extract it from tar...
tar -xv <filename>

3. configure the make file...
./configure

3a. if the last command seems to end okay then you just type 'make' and press enter. if it compiles you will be able to launch it in that directory by typing ./<application>

4. if all is well so far and you want to install it type 'make install' and press enter.

you might need to type './make' for the last two things. and if you want to start the make over you type "make clean" or something like that.. you can find the exact command for a clean make in the readme file.


you should also read the readme files that are created when you untar.  they will give you the specifics for the application your working with such as what directory to run ./configure and ./make in but basically its those 4 steps.

---

### Post by oldos2er on 2011-05-01
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by TheNewbieGeek on 2011-05-01
yes it does have a install.sh and I compiled it. Does compile mean it's runnable? If not can you explain what else needs to be done. Thank you.

---

