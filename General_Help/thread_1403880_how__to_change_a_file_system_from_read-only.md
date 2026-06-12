---
title: "how  to change a file system from read-only"
date: 2010-02-10
forum: General Help
---

### Post by mcsheffrey on 2010-02-10
I have sandisk usb and want to get rid of the "U3" partition that's on it, but its a read-only file system. can't chmod to 777 from root. Any help with this would be appreciated.
Thanks

---

### Post by Megafag on 2010-02-10
> **mcsheffrey said:**
> I have sandisk usb and want to get rid of the "U3" partition that's on it, but its a read-only file system. can't chmod to 777 from root. Any help with this would be appreciated.
Thanks

What filesystem is the partition?

EDIT: maybe this might help

[http://www.linuxquestions.org/questions/linux-hardware-18/removal-of-u3-crap-from-usb-flash-how-410539/](http://www.linuxquestions.org/questions/linux-hardware-18/removal-of-u3-crap-from-usb-flash-how-410539/)

there is something in there about a .exe that you can use to uninstall U3, which you could run in a virtual PC or maybe through wine.

---

### Post by mcsheffrey on 2010-02-10
Thanks, I downloaded the U3 uninstaller from there and that removed it. (Although I did have to run it on a windows machine, because when it ran on ubuntu, it couldn't find the sandisk)

---

### Post by Megafag on 2010-02-10
> **mcsheffrey said:**
> Thanks, I downloaded the U3 uninstaller from there and that removed it. (Although I did have to run it on a windows machine, because when it ran on ubuntu, it couldn't find the sandisk)

Sounds like its time to mark this thread resolved ;)

---

