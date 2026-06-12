---
title: "Unable to run simple programs in Wubi after installing gcc"
date: 2011-07-02
forum: General Help
---

### Post by catholala on 2011-07-02
I am a beginner of ubuntu.
I have installed Wubi in my machines. 
After that, I have installed gcc 4.5 and 4.6 respectively using sudo apt-get.[INDENT]sudo apt-get install gcc 4.5/ 4.6
sudo apt-get install gfortran
[/INDENT]also, I have installed csh and tcsh.[INDENT]sudo apt-get install csh
sudo apt-get install tcsh
[/INDENT]now, the problem is that I cannot even run a simple hello_world program which was saved on my Desktop.
[INDENT]gfortran hello_world.f95 -o hello_world
hello_world

[/INDENT]gfortran can compile the code into an executable file, but by typing hello_world in the terminal I cannot run the program. It was said the "File not found."

There are other problems like I cant use where to locate files. Is that because I have installed the wrong version of something since Wubi is an i686?

Thank you for your help!!

---

### Post by oldos2er on 2011-07-02
In a terminal, ```
cd Desktop

./hello_world
```

---

### Post by dino99 on 2011-07-02
for serious experience:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by catholala on 2011-07-03
My problems got fixed.
Thanks!!

---

