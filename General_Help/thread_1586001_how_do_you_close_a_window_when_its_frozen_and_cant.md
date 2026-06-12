---
title: "how do you close a window when its frozen and cant link it to a process?"
date: 2010-10-01
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-01
I installed JDownloader, ran it and it said it was updating. I pressed the X button to close that (there was no cancel button or anything) and it stopped the download progress yet is still there frozen. I can minimize/maximize/resize the window but cant close it. I have even looked for a process named JDOWNLOADER and its not there.

Further, I even uninstalled it by typing sudo apt-get remove jdownloader.

does anyone know how to close the window? or some way  to find the process (if it exists). I don't want to restart my computer as I have too many things open.

---

### Post by Ancanus on 2010-10-01
Open a console

```
$xkill
```

and click on your window.


I have it as a keyboard shortcut.

---

### Post by daimaru on 2010-10-01
you can list all running processes by entering in console (Applications->Accessories->Terminal):
**Method1:**
simple way use xkill. just type in terminal xkill and then click on the unresponsive window. 
```
xkill
```
if this does not work
**Method 2:**
```
ps aux
```
this gives you the process number for example 
```
ps aux | grep jdownloader
```
should return one line with the process id of jdownloader. you can then kill the app by typing
```
kill -9 <process id number>
```
if it requires root privileges type sudo in front of kill. If you know a programs name you can also use killall instead of the process id number.

---

### Post by fuzzylogic25 on 2010-10-01
omg that xkill function is so cool!!!!! im pretty sure windows didnt have that!

things like this make me so glad ive moved to ubuntu. thanks for the help guys!

---

