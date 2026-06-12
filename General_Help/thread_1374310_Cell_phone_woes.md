---
title: "Cell phone woes"
date: 2010-01-06
forum: General Help
---

### Post by theozzlives on 2010-01-06
My Samsung Delve used to connect to CDMA quite easily. My Blackberry Perl will only connect with my Windows 7 (in a VirtualBox). I need to connect it to Ubuntu, any help?

lsusb:```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0fca:8004 Research In Motion, Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Windows recognizes it as a Blackberry Smartphone

---

### Post by theozzlives on 2010-01-07
bump

---

### Post by GoldNugget on 2010-01-07
If you haven't tried it yet, install Blueman (its in the repositories) which allowed me to connect easily. Launch Blueman, right click on your connection, select Serial Port and then Dial up Service. Your mobile connection should now be listed in Network Manager. Note that it didn't show up in Wicd and so I had to remove it and use Network Manager.

Some others seem to have had luck using bbtether. Heres a thread about it: [http://ubuntuforums.org/showthread.php?t=1094322&highlight=tether+blackberry](http://ubuntuforums.org/showthread.php?t=1094322&highlight=tether+blackberry) 

I am using a Blackberry Curve, Ubuntu Karmic on an eeepc 900 with a cheap Cirago usb adapter.

Good luck and Happy New Year!

---

### Post by theozzlives on 2010-01-09
> **GoldNugget said:**
> If you haven't tried it yet, install Blueman (its in the repositories) which allowed me to connect easily. Launch Blueman, right click on your connection, select Serial Port and then Dial up Service. Your mobile connection should now be listed in Network Manager. Note that it didn't show up in Wicd and so I had to remove it and use Network Manager.

Some others seem to have had luck using bbtether. Heres a thread about it: [http://ubuntuforums.org/showthread.php?t=1094322&highlight=tether+blackberry](http://ubuntuforums.org/showthread.php?t=1094322&highlight=tether+blackberry) 

I am using a Blackberry Curve, Ubuntu Karmic on an eeepc 900 with a cheap Cirago usb adapter.

Good luck and Happy New Year!

Blueman's a BlueTooth Manager. I'm wanting to use my USB cable, not BlueTooth.

---

### Post by theozzlives on 2010-01-12
Come on, I'm to the point where I can remove Windows and VirtualBox from my laptop. The only thing stopping me is, I can't tether my BlackBerry Pearl to Linux. BBtether don't work and the onlything Blueman is good for is my Bluetooth. There's gotta be a way.

---

### Post by theozzlives on 2010-01-14
Bump

---

### Post by theozzlives on 2010-01-15
bump

---

### Post by theozzlives on 2010-01-16
Bump

---

