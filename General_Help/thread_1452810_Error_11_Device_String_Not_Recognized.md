---
title: "Error 11: Device String Not Recognized"
date: 2010-04-12
forum: General Help
---

### Post by HeretikSaint on 2010-04-12
The other day I was cruising the internet and found a thread that allowed a GUI for grubs boot menu.  I played around with it and followed the instructions, only to reboot and find the grub rescue prompt.  I did the "find /boot/grub/stage1" and "setup (hd0,3)" and the boot menu popped back up.  My Windows 7 part of the menu works find but when I try to load the Ubuntu part of the menu (or even the recovery portion), it tells me "Error 11: Device String Not Recognized" and tells me to hit "enter".  After hitting enter, it pops me back out at the boot menu.

Any idea where I go from here?  Or is my Ubuntu partion fried?

---

### Post by HeretikSaint on 2010-04-13
Can anyone please help me?  I would really like to recover my ubuntu partition.

---

### Post by hryanjones on 2010-04-14
About all I can do is give you a vote of confidence.  Your Ubuntu partition is almost certainly still there, it's just grub is failing to get to it.  I've had some problems with this in the past and it's not very fun.  To my knowledge Windows can't mount Linux (ext2/ext3) partitions so one way would be to attack it using a LiveCD boot.  You'll probably need to dig around in 
/etc/grub.d/ and /boot/grub/ (keeping in mind that they'll be mounted within a subdirectory when you're running from the live cd).  I'm quite sure it can be done, but it probably will take some digging.

Good Luck

---

### Post by john newbuntu on 2010-04-14
Instead of setup (hd0,3), try this at the rescue prompt:

```
root (hd0,3)
setup (hd0)
```

assuming your partition is proper.

---

