---
title: "ubuntu startup problem, NEED HELP"
date: 2011-12-14
forum: General Help
---

### Post by ballinitup on 2011-12-14
Hello I successfully installed Ubuntu 11.10 64-bit on my Dell Inspiron M5030 laptop. But whenever I try to boot up it just goes to either a black screen with the mouse pointer or the default background with the mouse pointer. I have tried to re-install, tried a different cd, and tried a different file and it's the same result. Please help me, I will type in any commands etc. Thanks.

---

### Post by jimmydean886-2 on 2011-12-14
It looks like your problem is LightDM. I suppose that on some obscure machines it may not work right. Simply hit ctrl+alt+f1, enter your username and password, then type:
```
sudo apt-get install gdm
```If you don't get a square window on your screen, type:
```
sudo dpkg-reconfigure gdm
```then select "GDM" as your default display manager.
Now type ```
 sudo shutdown -r now
``` and your system should boot fine.

---

### Post by ballinitup on 2011-12-14
Ok thank you and should I press the key command when it is at the blank screen?

---

### Post by ballinitup on 2011-12-15
Hey I just changed it to gdm and it still does the same thing.... Any other options?

---

### Post by BC59 on 2011-12-15
Look here if you belong to this category:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

