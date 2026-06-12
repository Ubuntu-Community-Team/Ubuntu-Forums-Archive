---
title: "need help!!!"
date: 2006-03-20
forum: General Help
---

### Post by mykelm03 on 2006-03-20
im a newbie here and i've just installed kubuntu...my question is, why is that my display is 640x480??? and there's no way i can change it into a much higher resolution...what shall i do???ive tried right click and go to configure desktop, display, but there's no other choice other than 640x480...my vga is nvidia geforce 4 mx 4000...thanks...

---

### Post by haaglin on 2006-03-20
have you installed the nvidia drivers?

---

### Post by Gustav on 2006-03-20
try typing this in the terminal and follow the instructions:
```
sudo dpkg-reconfigure xserver-xorg
```
if that doesn't work, look at this:
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by mishranurag on 2006-03-20
The important thing is that when you follow the instructions using the following command by Gustav, and you get to the point where you have to choose the resolution of the screen, only choose the relevant option and deselect all the unrelevant resolutions.

Anurag
[quote=Gustav]try typing this in the terminal and follow the instructions:
```
sudo dpkg-reconfigure xserver-xorg
``` if that doesn't work, look at this:
[http://www.ubuntuforums.org/showthread.php?t=83973]("http://www.ubuntuforums.org/showthread.php?t=83973")[/quote]

---

