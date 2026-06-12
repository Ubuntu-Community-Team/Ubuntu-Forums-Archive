---
title: "Why is my computer running in low graphics?"
date: 2010-06-06
forum: General Help
---

### Post by CharlesJWelsh on 2010-06-06
I have no idea how to change it... im runing 10.04.

---

### Post by Forged on 2010-06-06
Has it always been like that or did it change when you updated?  What kind of graphics card do you have?

---

### Post by Spr0k3t on 2010-06-06
Hardware details of your system would help.  Also, might need to see the dmesg to track down where the problem is.

---

### Post by CharlesJWelsh on 2010-06-06
if you could tell me how to get you that info i would gladly <:]

---

### Post by Forged on 2010-06-06
go to terminal and type
lspci

what comes up under VGA compatible controller.

You also might want to try typing this into a terminal and seeing if it works
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by CharlesJWelsh on 2010-06-06
[QUOTE=Forged;9420601]go to terminal and type
lspci

what comes up under VGA compatible controller.

Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)

---

### Post by diesch on 2010-06-06
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution) and [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) may help

---

### Post by Forged on 2010-06-06
then try 
```
sudo dpkg-reconfigure xserver-xorg
```
restart and see if that helps

---

### Post by diesch on 2010-06-06
> **Forged said:**
> then try 
```
sudo dpkg-reconfigure xserver-xorg
```restart and see if that helps

In recent versions of Ubuntu this doesn't help as X.org dioesn't use xorg.conf anymore by default.

---

### Post by davidmohammed on 2010-06-06
given that you are using 855GM graphics I presume you must have done something to get lucid to boot e.g. added i915.modeset=1 to grub / down graded your kernel / something else?

Have you recently upgraded and this was an issue on the upgrade?
 If so suggest rename /etc/X11/xorg.conf to something else and make sure you boot with

i915.modeset=1

---

### Post by CharlesJWelsh on 2010-06-07
Yes I had to use i915.modeset=1 ... But I'm not following what you are telling me to do... I am not very experienced with ubuntu...

And i have the "Xserver- Xorg" on my administration tab. It said it was a GUI but I have no idea what does what. -.- So i left it alone...

---

### Post by davidmohammed on 2010-06-08
ok,
 open a terminal and type the following

ls /etc/X11/xorg.conf

if an error "no such file or directory" is display then you don't have this file.

if a file is displayed, then type the following

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

reboot

---

