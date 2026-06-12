---
title: "nautilus: unable to determine program to run"
date: 2009-08-24
forum: General Help
---

### Post by capitanomalley on 2009-08-24
Hello,

I am having trouble running program from nautilus. 

when I:
right click program file -> Open as Administrator

I get the error:
Unable to determine program to run.
Item you selected cannot be open with administrator powers because the correct
application cannot be determined.

but when I go from the terminal:
./program

It executes fine.
I also did 'chmod 777' program for permissions.

I don't understand how I can be getting this error.

---

### Post by zkriesse on 2009-08-24
What program are you trying to run exactly?

---

### Post by capitanomalley on 2009-08-24
it has no extension but
according to properties it is a:
executable (application/x-executable)

---

### Post by dumblebee100 on 2009-08-24
I think that if you select something from the right click ..it searches for applications which can read that file 
in your case ./program ...
how can you load that program with other program ..

if that's a script then open with terminal with administrator powers ..


lets suppose u have a .txt file ..and u selected it with right click 
then list of programs appear which can read that type of mimetype 

since u have ./program 
which is a executable ..it can be opened directly ( just click on it ) or from terminal ..if you are from terminal u can run it with sudo powers like 
```
sudo path_to_program/program
```

if u want to execute from nautilus and with administrator powers then u have to open it from 
```
sudo nautilus 
```

because a executable cannot be ececuted by another executable ....
It can be only be opened with different executables 

if u really want different access then use sudo from terminal or sudo nautilus if u want gui

get the difference between opening and executing ..

one cant execute gedit from gedit itself ...even though u have source code for it ..u can just open it from gedit but cant run in gedit ..

your problem is simialr I think so

---

### Post by utnubuuser on 2009-08-24
shouldn't it be gksu nautilus instead of sudo nautilus?

---

### Post by dumblebee100 on 2009-08-24
> **utnubuuser said:**
> shouldn't it be gksu nautilus instead of sudo nautilus?

Its correct in your case if you use gui for entering password

I even open root nautilus from terminal itself ...so I use that command ...

anyways did u understand what this user's problem is ...Im not getting a clear idea of it so I wrote what all I understand

---

### Post by capitanomalley on 2009-08-24
Thanks for replies. To be clear it was user program on desktop I simply wanted to double click and run. I figured it out, one of the files the program depended on had restricted permissions. Does nautilus not show those errors?

I don't know why the 'open as administrator' option didn't work for it however, since it would have had root permission and then access to the more restricted file that the program depended on.

---

