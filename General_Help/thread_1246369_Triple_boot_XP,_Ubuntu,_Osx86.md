---
title: "Triple boot XP, Ubuntu, Osx86"
date: 2009-08-21
forum: General Help
---

### Post by Thoork on 2009-08-21
Hey,

So I was wondering if its possible to modify and make the boot screen show all the three options. The way it is right now is the following: I can choose between several ubuntu 'versions' (recovery mode, etc) and at the end microsoft windows. Within windows, I can choose mac or windows, but going into mac i get yet another screen. Its not very handy. Is there a program that could help me to do that?

Thanks,

Guillem.

---

### Post by enli on 2009-08-21
If you are new, Post the output of "sudo fdisk -l"

Else you can simply copy paste the windows grub options into new menu item. Just need to change the root option.

---

### Post by kaptain0 on 2009-08-21
did you use an OSx86 distro, or patch-install an actual install disc?
 
just curious.

---

### Post by Thoork on 2009-08-21
> **enli said:**
> If you are new, Post the output of "sudo fdisk -l"

Else you can simply copy paste the windows grub options into new menu item. Just need to change the root option.

Here it is ;)   :

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc79705e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10747    86325246    7  HPFS/NTFS
/dev/sda2           10748       24321   109033155    f  W95 Ext'd (LBA)
/dev/sda5           16673       24321    61440561   af  Unknown
/dev/sda6           10748       10769      176652   82  Linux swap / Solaris
/dev/sda7           10770       16672    47415816   83  Linux

Partition table entries are not in disk order


kapitain0, I used an actual install disk.

Thanks!

---

### Post by enli on 2009-08-21
Type in terminal,
```

sudo gedit /boot/grub/menu.lst

```

and paste following lines at the end of the file
```

title 		Apple Mac OS X
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1	

```

Reboot and see if it boots mac. If not try changing in above file
```

rootnoverify	(hd0,5)

```

---

### Post by Thoork on 2009-08-21
> **enli said:**
> Type in terminal,
```

sudo gedit /boot/grub/menu.lst

```and paste following lines at the end of the file
```

title         Apple Mac OS X
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader    +1    

```Reboot and see if it boots mac. If not try changing in above file
```

rootnoverify    (hd0,5)

```

Thanks a bunch, i'll try that and share the results.

---

