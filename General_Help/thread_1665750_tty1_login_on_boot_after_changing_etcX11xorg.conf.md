---
title: "tty1 login on boot after changing etc/X11/xorg.conf"
date: 2011-01-12
forum: General Help
---

### Post by Durn Whippersnapper on 2011-01-12
So I'm trying to get two fingered scrolling on my Ubuntu 10.10 netbook. According to advice from
[http://ubuntuforums.org/showthread.php?t=516798](http://ubuntuforums.org/showthread.php?t=516798)
I created an xorg.conf file in etc/X11 and put 

Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"

in the file. I restarted my computer, and now it comes up with

Ubuntu 10.10 [Computer name] tty1

[Computer name] login:



Not only has this not happened before, I have no idea what to put for my username and password. Any help is greatly appreciated.

---

### Post by davidmohammed on 2011-01-12
suggest reboot - just after the netbook boots, press and hold shift.  This should display your grub.  Choose the recovery kernel.  When prompted choose to start with fail-safe graphics.  This should allow you to get to a graphical screen to allow you to remove/edit the xorg.conf file.

---

### Post by WorMzy on 2011-01-12
If you didn't have an xorg file before, simply remove it by logging in to the tty and running

```
sudo rm /etc/X11/xorg.conf
```

You can then start the GUI by running

```
sudo service gdm start
```

---

### Post by Durn Whippersnapper on 2011-01-12
Alright, I booted in safe mode and just deleted the xorg.conf file, and everything's back to normal. Now to figure out how to get two finger scrolling. Thanks a lot!

---

