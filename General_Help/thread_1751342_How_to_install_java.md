---
title: "How to install java"
date: 2011-05-06
forum: General Help
---

### Post by Nerijus1 on 2011-05-06
Hi all!, i recently downloaded ant installed "Ubuntu 11.04" (i think so), and i need to install java JDK to it, i write

```
sudo apt-get install sun-java6-jdk sun-java6-jre
```But it says:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```so, how can i download it? thanx for helping, and sorry for my english if i made mistakes :rolleyes:

---

### Post by chellrose on 2011-05-06
Do you have a package manager (such as Synaptic) open concurrently?  The terminal command won't work if a package manager or updater is also running.

---

### Post by Nerijus1 on 2011-05-06
No, i'm beginner in ubuntu, but i try to download "Synaptic" right now if i find it.
And also, how to disable this? It's wery uncomfortable :(
[URL="http://img593.imageshack.us/i/screenshothbx.png/"]http://img593.imageshack.us/i/screenshothbx.png/

[/URL][LEFT][ ]("http://img593.imageshack.us/i/screenshothbx.png/")Sorry for my dumb questions, i found "Synaptic" installed, opened it and i installed there java JDK and JRE, and now eclipse works fine, thanx for helping ;)
[/LEFT]
[URL="http://img593.imageshack.us/i/screenshothbx.png/"] 
[/URL]

---

### Post by ajgreeny on 2011-05-06
> **Nerijus1 said:**
> 
And also, how to disable this? It's wery uncomfortable :(
[URL="http://img593.imageshack.us/i/screenshothbx.png/"]http://img593.imageshack.us/i/screenshothbx.png/

[/URL][LEFT]Sorry for my dumb questions, i found "Synaptic" installed, opened it and i installed there java JDK and JRE, and now eclipse works fine, thanx for helping ;)
[/LEFT]
[URL="http://img593.imageshack.us/i/screenshothbx.png/"] 
[/URL]There are very few dumb questions, only dumb answers; if you don't know how to do something, ask!

To disable the unity desktop you can logout and then login again.  After choosing the username, a session menu will appear bottom right where you can choose the "classic desktop" or some similar description.  That will get you back to the gnome desktop from previous versions of ubuntu.

---

### Post by Nerijus1 on 2011-05-06
> **ajgreeny said:**
> There are very few dumb questions, only dumb answers; if you don't know how to do something, ask!

To disable the unity desktop you can logout and then login again.  After choosing the username, a session menu will appear bottom right where you can choose the "classic desktop" or some similar description.  That will get you back to the gnome desktop from previous versions of ubuntu.

Thanx, but now i'm stuck with .sh files executing, i write ./database_installer.sh and getting error:

```
bash: ./database_installer.sh: /bin/bash^M: bad interpreter: No such file or directory

```

---

### Post by ajgreeny on 2011-05-07
When you type that command are you in the folder where the .sh file resides?  As an example, if the .sh is on your desktop use ```
cd Desktop
``` then ```
./database_installer.sh
``` and see if that works.  Assuming that the .sh file is marked as executable it should run.

---

### Post by Spyderkid on 2011-05-07
basically the trouble was that you had ubuntu software center or a package thing open. or when you've used sudo for another command

---

