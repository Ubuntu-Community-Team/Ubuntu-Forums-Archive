---
title: "Login screen fix"
date: 2010-06-19
forum: General Help
---

### Post by tish371 on 2010-06-19
Can anyone please help me fix this? Ubuntu 10.04. I have fglrx driver installed.. It appears when i set the resolution to anything higher than 1024x768... the login screen background is messed up to
[[IMG]http://img138.imageshack.us/img138/6811/fixthiss.th.png[/IMG]]("http://img138.imageshack.us/i/fixthiss.png/")

---

### Post by dcstar on 2010-06-19
> **tish371 said:**
> Can anyone please help me fix this? Ubuntu 10.04. I have fglrx driver installed.. It appears when i set the resolution to anything higher than 1024x768... the login screen background is messed up to


That is not the "login screen" background, that is your desktop background.

Right-click anywhere in it and select the Change Desktop Background choice, you will see what to do then.

---

### Post by tish371 on 2010-06-19
I know its a screen shot from my desktop. Read carefully.... "the login screen background is messed up to", and the image is to show how its messed up.... 

Its a resolution kinda problem... when i boot my computer it looks like that...  i have to use 
xrandr --output CRT1 --mode 1280x1024 after that the the desktop screen and the login screen looks normal .... but when i reboot its messed up once again

ive tried to add the xrandr --output CRT1 --mode 1280x1024 line to /etc/gdm/Init/Default, but that didn't help

---

