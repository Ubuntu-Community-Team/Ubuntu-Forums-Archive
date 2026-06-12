---
title: "shell script problem"
date: 2011-05-25
forum: General Help
---

### Post by reggs on 2011-05-25
Hi, everybody!
i have a little script to run some programs:
```
/home/hackmaster/programs/jambi/bin/juic -pfUi  -p rplus.gui ./MainWindow.jui
```
the script is in the same folder as MainWindow.jui is, which is subfolder of $HOME.
the problem is - when i run the script i get error:
```
juic: failed to read file: /home/hackmaster/javaworkspace/Rplus/src/MainWindow.jui
```
while executing the same command from the shell runs excellent.

what am i doing wrong?
p.s. i know similar question was discussed in the forum but the problem has not been solved.

---

### Post by LordNeo on 2011-05-25
My guess is that the program is not aware of the path where you are calling from.
Try to use absolute paths in your script and it should work ok

---

### Post by reggs on 2011-05-27
I've already tried to run the script from its folder - it's no use(
I've tried this:
```
cd /home/hackmaster/javaworkspace/Rplus/src/
/home/hackmaster/programs/jambi/bin/juic ./MainWindow.jui
```
and got error:
```
can't cd to: /home/hackmaster/javaworkspace/Rplus/src/
```
If i put #!/usr/bin/bash to the beginning of the script it says something about bad interpreter (i'm now far from my ubuntu note and don't remember it exactly). What could that be?
Anyway, thak you for your tip, i'll try it as soon as i can.

---

### Post by Pand5461 on 2011-05-27
> **reggs said:**
> 
If i put #!/usr/bin/bash to the beginning of the script it says something about bad interpreter (i'm now far from my ubuntu note and don't remember it exactly). What could that be?

Just incorrect path to interpreter. It's in /bin/bash by default, not /usr/bin/bash.

---

