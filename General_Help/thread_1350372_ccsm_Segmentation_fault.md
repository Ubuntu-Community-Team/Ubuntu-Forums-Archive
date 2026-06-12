---
title: "ccsm Segmentation fault"
date: 2009-12-09
forum: General Help
---

### Post by bioliu on 2009-12-09
I have a tiny problem ... and since I do not know enough about Ubuntu it is hard for me to know where to look to fix ....

There is an error when I start "compizconfig settings manager":

[COLOR=DarkGreen]liumin@liumin-laptop:~$ ccsm
Segmentation fault[/COLOR]

I have no idea what's wrong.

---

### Post by byStanderone on 2009-12-09
...don't know if this would help: sudo rm /var/cache/apt/*.bin

this removes the binary clutter of an incomplete or failed program install.

---

### Post by bioliu on 2009-12-09
thank you! but the problem still existed!

---

### Post by Kevbert on 2009-12-09
Rather than using 'rm' you should use the command
```
sudo apt-get clean
```
to clean out the cache (rm when used wrongly could trash your system).

What is the make and model of your display adapter ? 
Has ccsm ever worked ?

---

### Post by bioliu on 2009-12-09
the window of "compizconfig settings manager" appear normally...then close in several seconds!
intel

---

### Post by Kevbert on 2009-12-09
Please enter the following in terminal
```
sudo lshw -C display
```
and post back. This will give us more information on your intel display adapter. If it is a GMA500 you may have some problems getting Compiz to work.

---

### Post by bioliu on 2009-12-10
the problem has been resolved...
I reinstall the system and try again...there is any error in this time!
I have no idea what's happened.

Thanks for your attention!--bioliu

---

### Post by byStanderone on 2009-12-10
...thanks kevbert, you got your point.

---

