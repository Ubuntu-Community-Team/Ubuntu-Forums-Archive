---
title: "USB not recognised on Ubuntu"
date: 2011-08-25
forum: General Help
---

### Post by stamatiou on 2011-08-25
Hey guys,
my laptop doesn't see none of my usb devices, I tried them on another computer and they worked. Also my usb flash drive has a little light on it so whenever I plug it in it blinks but in this computer it does not blink! I do not know if it helps but I have recently installed Virtual Box and when I run the command sudo lsusb I take 
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by nomko on 2011-08-25
Did you add yourself to the vbox user group?? If not, do this:
 
Open a terminal and type in: **sudo gedit /etc/groups**
type your password
the file will be opened and search for a line which starts with vbox
At the end of that line type your username, as example: vbox:x:{number}:[username]
 
Then you must restart your computer. Check if you still have problems with USB.

---

### Post by stamatiou on 2011-08-25
> **nomko said:**
> Did you add yourself to the vbox user group?? If not, do this:
 
Open a terminal and type in: **sudo gedit /etc/groups**
type your password
the file will be opened and search for a line which starts with vbox
At the end of that line type your username, as example: vbox:x:{number}:[username]
 
Then you must restart your computer. Check if you still have problems with USB.
My user is already there :confused: But the problem is on the real computer not on the virtual envirmoment

---

### Post by nomko on 2011-08-25
I know that it is not your virtual environment, i gave you this solution because you meantioned that you recently installed VirtualBox, and i quote:
> I do not know if it helps but I have recently installed Virtual Box 
So i thought it had to do with VirtualBox. 
 
Try searching this forum, i know more folks had similar problems and they all get solutions.

---

### Post by raja.genupula on 2011-08-25
[http://ubuntuforums.org/showthread.php?t=204168](http://ubuntuforums.org/showthread.php?t=204168)
or
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by stamatiou on 2011-08-25
Thank you guys now that I plugged it in it works! :confused::confused:

---

### Post by Darth Trix on 2011-08-29
I've the same problem. It doesn't even detects my mouse

---

