---
title: "sandisk 4gb usb"
date: 2010-03-11
forum: General Help
---

### Post by 762sks on 2010-03-11
i have a sandisk and this stupid u3 software keep popping up. ive tried to remove it using the disk utility, it see the section with the u3 stuff on it, but it wont let me format that section or even delete the files. 

i am doing this because i wanna use this to put ubuntu on a bootable live disk on there. 




thanks

---

### Post by viralmeme on 2010-03-11
> **762sks said:**
> i have a sandisk and this stupid u3 software keep popping up ..
That's becasue the U3 stuff is in a hidden partition that's marked as a CD. You can DD the whole drive. But I had problems getting a U3 USB device to boot, same with a HP device. It appears to be pot luck as to which will boot.

[http://linuxgazette.net/issue55/tag/20.html](http://linuxgazette.net/issue55/tag/20.html)

---

### Post by Arndtwe on 2010-03-11
I have had no trouble with with Sandisk USB drives... I have had three or four of them and all have worked fine. Removing the U3 software was simple. Using a Windows box, plug in the thumb drive, then after the U3 stuff starts, go into the U3 menu, I do not recall exactly where, but there is the option to un-install and remove U3. Then if you format the drive it will be completely gone. To use it as a live thumb drive, just make it bootable and put whichever iso you want on it.

---

### Post by sgosnell on 2010-03-11
Or just fire up gparted and delete the partition, then expand the primary partition to include everything.

---

### Post by 762sks on 2010-03-11
ok got it thanks guys.

---

