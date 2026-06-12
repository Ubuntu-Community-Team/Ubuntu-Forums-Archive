---
title: "Problem after inappropreate shutdown"
date: 2012-01-08
forum: General Help
---

### Post by gentao88 on 2012-01-08
I was doing some heavy stuff and my netbook froze. So, I shut it down by the hardware button. When I tried to log back in, the lock screen was different and after the login, my background was orange, my desktop icons were different and the launch bar had disappeared. What should I do? Ubuntu 11.10.

Two screenshots:
[http://img843.imageshack.us/img843/5377/p1080988a.jpg](http://img843.imageshack.us/img843/5377/p1080988a.jpg)
[http://img560.imageshack.us/img560/5003/p1080987c.jpg](http://img560.imageshack.us/img560/5003/p1080987c.jpg)

---

### Post by LinuxFan999 on 2012-01-08
The problem in image 1 appears to be extremely common.
 
After logging in, open the terminal with Ctrl-Alt-T (If that doesn't work, try Ctrl-Alt-F1), then type this:
```
unity --reset
``` (If unity --reset doesn't work, try typing unity --replace instead)
 
If you used Ctrl-Alt-F1 to get to the terminal, press Ctrl-Alt-F7 to return to the desktop.
 
Another thing you can try is installing another desktop environment, like KDE or XFCE.
```
sudo apt-get install kde4
```
```
sudo apt-get install xfce4
```
 
After installing a desktop environment, you can also install another X display manager, like KDM or GDM, and remove LightDM.
```
sudo apt-get install kdm
```
```
sudo apt-get install gdm
```
```
sudo apt-get remove lightdm
```
 
If neither of these suggestions work, you will need to back up your data and reinstall Ubuntu.

---

### Post by gentao88 on 2012-01-08
Unfortunately none of these suggestions work :(
I still have the same problem after installing kdm.
So, I will have to reinstall ubuntu.
Thanks a lot for your suggestions :)

---

