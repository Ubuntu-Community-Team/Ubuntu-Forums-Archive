---
title: "Crashed Gnome 3"
date: 2011-12-07
forum: General Help
---

### Post by lymera1n on 2011-12-07
I am on Ubuntu 11.10 an run Gnome 3 Shell as my default desktop interface.

I accidentaly ran "metacity --replace" and my desktop crashed. Whenever it turns on, a bunch of words flow across the screen, it flickers three times, and x doesnt start. What do I need to do to fix this fatal error?

---

### Post by josephmills on 2011-12-07
boot a live cd then run ```
sudo fdisk -l 
```

to locate the sda'whatever' that ubuntu is installed on. then 
```
mount /dev/sda<ubuntu partition> /mnt/ 
```
exsample 
fdisk -l 
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050e11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2630    21123505+  83  Linux
/dev/sda2            2630        3156     4219905    5  Extended
/dev/sda3   *        3156        9730    52805632    7  HPFS/NTFS
/dev/sda5            2631        3142     4106240   82  Linux swap / Solaris

```


as you can see ubuntu is installed on sda1 for me
so for me it would be 
```
mount /dev/sda1 /mnt/
```



then cd into /mnt/ 
and ls 
Is it mounted ? 
if so run command ```
sudo chroot /mnt/ 
```
then install or uninstall/ fix it :D

---

### Post by lymera1n on 2011-12-07
I can run "startx" in tty1 and x works, but its unity2d. Is there something i can do to undo the command i ran and get everything working normally.
And "halt" doesn't work.

---

