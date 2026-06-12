---
title: "GRUB Error 13 help"
date: 2009-10-23
forum: General Help
---

### Post by drshockter on 2009-10-23
Hello so I get the error 13 when I try to boot Windows XP
I searched the fourms and found people wint similar problems and it didnt help

I have 2 Hard Drives

Master(100 GIG) Windows XP
Slave(320GIG) Ubuntu

I know how to change the menu.lst and save it

by deafault it is set like this

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
map        (hd1) (hd0)
map        (hd0) (hd1)
chainloader    +1


and I tried changing it to this

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


I also tried deleting the boot.ini in the windows HD didnt help and I replaced it

Thank you in advance

---

### Post by uncle-c on 2009-10-23
Try this.

```

title Windows XP
root (hd1,0)
map (hd1,0) (hd0,0)
map (hd0,0) (hd1,0)
makeactive
chainloader +1

```

---

### Post by drshockter on 2009-10-23
Nope same error 13 message(what the heck)

Could it possibly be this

      # This entry automatically added by the Debian installer for a non-linux OS
This# on /dev/sdb1

---

### Post by uncle-c on 2009-10-23
Are you sure that XP is on your secondary hard drive ? When you start using "map" in grub that means it is on the secondary drive. We need to know your disk / partition layout.
Could you kindly  post the output of

```

$ sudo fdisk -l

```

---

### Post by drshockter on 2009-10-23
Solved (woohoo)

like I thought I had to change to this

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda
title              Windows XP
root               (hd0,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


Thank you though

---

