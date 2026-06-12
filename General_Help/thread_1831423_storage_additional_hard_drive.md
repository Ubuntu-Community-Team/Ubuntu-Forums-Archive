---
title: "storage /additional hard drive"
date: 2011-08-23
forum: General Help
---

### Post by gringo8217 on 2011-08-23
hi guys
i was wondering when installing a second hdd what program to use or any recomeded software to be used and what format to use ? ntfs / fat 32 etc or ? as new user to linux and ubuntu this is a whole knew ball game from windows so i hope one of you guys can lend me a hand my version is 11.04 :KS

---

### Post by frankbooth on 2011-08-23
Just plug it in as you would with Windows :). If you run into trouble, make sure it's detected in BIOS before troubleshooting. You can also ask us for help here on the forums if you need any.

You can format and partition it with [GParted]("http://gparted.sourceforge.net/") (install it through the Software Center) and you'll be fine by formatting it to *ext4*, Ubuntu's default file system.

---

### Post by aeiah on 2011-08-23
use gparted to format it in ubuntu. if you want windows to access it at any point, format as NTFS. if you don't, go with ext4

---

### Post by gringo8217 on 2011-08-23
thanks for the replys !!

---

### Post by gringo8217 on 2011-08-23
i see that i have G parted installed from where do i access it through terminal as i cannot see as a program in the application menu ?

---

### Post by frankbooth on 2011-08-23
You can launch it through the terminal like this:
```

gksudo gparted

```
This will launch GParted with administrative privileges.

---

### Post by gringo8217 on 2011-08-23
thank you all done and installed !! appreciate your time !

---

