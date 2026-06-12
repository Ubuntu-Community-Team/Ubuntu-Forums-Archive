---
title: "I need help installing Penumbra"
date: 2010-06-02
forum: General Help
---

### Post by cygnis1 on 2010-06-02
Hi everyone.  I downloaded the demo of Penumbra Overture, it is a .sh file (113Mb).  I can't open the file.  In a terminal I ran chmod +x PenumbraOvertureDemo-2553.sh  and then sudo ./PenumbraOvertureDemo-2553.sh and I get an error "./PenumbraOvertureDemo-2553.sh: 2: Syntax error: "(" unexpected" .  The quotation marks are my own.  Is the file corrupted?  One of my lugmates thinks it might be a shar file, but Karmic says that it is a shell script.  Another friend says that it is too large to be a shell script.  Can anyone help?  Here is the code:

john@john-laptop:~$ cd /home/john/00
john@john-laptop:~/00$ chmod +x PenumbraOvertureDemo-2553.sh 
john@john-laptop:~/00$ sudo ./PenumbraOvertureDemo-2553.sh 
[sudo] password for john: 
./PenumbraOvertureDemo-2553.sh: 2: Syntax error: "(" unexpected
john@john-laptop:~/00$ 

Thanks

---

### Post by fooman on 2010-06-02
i think you may need to add an "sh" in between the sudo and ./....like so:

```
sudo sh ./PenumbraOvertureDemo-2553.sh
```

see if that works.

---

### Post by cygnis1 on 2010-06-02
I tried that with the same results.  Thanks anyway.

---

### Post by fooman on 2010-06-02
i have downloaded the file myself and tried with the "sh" like i said and without the "sh"...

both work fine here.

try right-clicking on the file itself > properties > permissions  ....and put a check next to "allow executing file as program".

then try again.

sorry if no help.

---

### Post by cygnis1 on 2010-06-02
I downloaded the program from another site and it works just fine.  Thanks to all.
Cygnis1

---

