---
title: "Identify block devices on your system.  How is it done"
date: 2009-08-17
forum: General Help
---

### Post by sefs on 2009-08-17
Hi all,

I have a system with a HD, some USB slots and some memory cards slots


How can I identify them by /dev/hdx ect.

I've stuck a memory stick pro in one of the slots but i dont know which /dev/xxx it is. 

Thanks.

---

### Post by 3rdalbum on 2009-08-17
It's quite easy. Issue this command in the terminal:

```
sudo fdisk -l
```

It will list all partitions from all connected devices. You can identify which is which by some common sense, the filesystem formats and the sizes of each partition (for instance, /dev/sda is most likely to be your hard disk, because it is the first device (a) to be detected on bootup and added to /dev).

I'm sure someone will post about some way to find it out through a GUI in Gnome, but I don't have any external devices at hand to try it out with :-)

---

### Post by sefs on 2009-08-19
Thanks for that!

---

