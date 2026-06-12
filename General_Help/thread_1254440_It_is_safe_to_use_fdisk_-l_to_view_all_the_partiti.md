---
title: "It is safe to use fdisk -l to view all the partitions connected to the computer right"
date: 2009-08-31
forum: General Help
---

### Post by billdotson on 2009-08-31
If I run fdisk -l that isn't going to cause any filesystem damage correct? If I were to actually use fdisk to partition something though it would. I don't know where but I have it in my head that I have to umount -a before using fdisk. I usually just open gparted to see what is mounted on what but that takes longer.

---

### Post by drs305 on 2009-08-31
Yes, it is safe. If you are interested in what a command or a switch does, open a terminal and type "man <command name>".
Example: man fdisk

You may want to run this command as "sudo fdisk -l"

---

### Post by howefield on 2009-08-31
> **billdotson said:**
> If I run fdisk -l that isn't going to cause any filesystem damage correct?

Running the command fdisk -l won't do any damage to your machine, it will only print out your disks/partitions configuration.

---

### Post by stderr on 2009-08-31
When you look at *man fdisk* you may notice that to get it do actually do something other than output info, you'll have to run fdisk, poke around its menu system, make changes, and tell it to save those changes before it does anything :) -l is pretty harmless

---

### Post by billdotson on 2009-09-01
I didn't see anything about mounting or unmounting in the man file.

---

### Post by drs305 on 2009-09-01
> **billdotson said:**
> I don't know where but I have it in my head that I have to umount -a before using fdisk. I usually just open gparted to see what is mounted on what but that takes longer.

> I didn't see anything about mounting or unmounting in the man file. 

You can use the following to see what is currently mounted:
```
mount
```

*fdisk* shows partitions.

---

