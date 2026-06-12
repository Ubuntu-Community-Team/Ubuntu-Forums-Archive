---
title: "configuring wacom pen pressure sensitivity"
date: 2011-09-28
forum: General Help
---

### Post by Awesomebill on 2011-09-28
After upgrading to Natty I've been having issues with my wacom pen tablet being too sensitive. I have to draw feather light just to get any line variation. I'm running xf86-input-wacom v. 0.11.x. if it helps

---

### Post by Favux on 2011-09-28
Hi Awesomebill,

Which model do you have?  It's on the back of the tablet.  Let's also look at the product ID.  Post the Wacom line in the output of the commmand ***lsusb*** in a terminal.

---

### Post by Awesomebill on 2011-09-29
Hi Favux,

 The model # is CTL-460 and lsusb gives me

```
Bus 008 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 056a:00d4 Wacom Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Favux on 2011-09-29
OK, that's a kernel bug.  The wrong value for the Bamboo Pen's pressure levels were used.  That was fixed upstream in the kernel and I think they are backporting the fix to Oneiric.  I don't know about Natty.  In the meantime to get a wacom.ko (the usb kernel driver) that has the correct pressure levels value you'll need to use input-wacom-0.11.1.  Instructions for compiling input-wacom are in part I. of the BambooPT HOW TO:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

---

### Post by Awesomebill on 2011-09-29
Thanks again Favux. You are a lifesaver.

---

