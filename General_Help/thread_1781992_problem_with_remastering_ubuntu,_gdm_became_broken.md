---
title: "problem with remastering ubuntu, gdm became broken"
date: 2011-06-14
forum: General Help
---

### Post by MrDrakonest on 2011-06-14
[COLOR=#000000][FONT=Times New Roman][COLOR=#888888][FONT=arial][COLOR=#000000]first of all, I  boot with my ubuntu os normally, after that I tried remastering using Ubuntu UCK,  I run the UCK, and follow the instructions there, my remastering  does not work, then I repeated the process, there is an error message that tell my disk is full, but I think my harddrive is large enough to accommodate more than 10Gb of data, and then when I was attempting to reduce the capacity of my hard drive, I found a new partition which seems to result from the remastering, I try to format new partition that who knows, remastering can be repeated, but in the fact, it's same(the error message tell that my disk is full), so i try to reboot to see the results. when I enter login window, I don't know what's wrong why my Ubuntu display so ugly, and the error message at the top right corner of the desktop manager who stated that I did not installed correctly, I try to login, but It's only a blank screen, after a moments, it's return to login screen
desktop manager that I use is a gnome,  and the distro is Ubuntu Maverick

help!:([/COLOR]

[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by MrDrakonest on 2011-06-14
anyone, need help please, I don't what should I do

---

### Post by ezsit on 2011-06-14
I would boot with a live CD, rescue any data you have, and reinstall. You can wait for advice on how to diagnose the problem, but saving your data and reinstalling usually takes less time.

---

### Post by wildmanne39 on 2011-06-15
> **MrDrakonest said:**
> [COLOR=#000000][FONT=Times New Roman][COLOR=#888888][FONT=arial][COLOR=#000000]first of all, I  boot with my ubuntu os normally, after that I tried remastering using Ubuntu UCK,  I run the UCK, and follow the instructions there, my remastering  does not work, then I repeated the process, there is an error message that tell my disk is full, but I think my harddrive is large enough to accommodate more than 10Gb of data, and then when I was attempting to reduce the capacity of my hard drive, I found a new partition which seems to result from the remastering, I try to format new partition that who knows, remastering can be repeated, but in the fact, it's same(the error message tell that my disk is full), so i try to reboot to see the results. when I enter login window, I don't know what's wrong why my Ubuntu display so ugly, and the error message at the top right corner of the desktop manager who stated that I did not installed correctly, I try to login, but It's only a blank screen, after a moments, it's return to login screen
desktop manager that I use is a gnome,  and the distro is Ubuntu Maverick

help!:([/COLOR]

[/FONT][/COLOR][/FONT][/COLOR]
Hi, you can try these commands
```
sudo apt-get remove --purge gdm
```
```
sudo apt-get install gdm

```
```
sudo apt-get install -f
```you will need to boot into recovery mode here is a link on how to do that.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
If this does not work boot a livecd and click try then run this script and post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by wildmanne39 on 2011-06-15
Hi, if you need more help post back here and we will help you.

---

