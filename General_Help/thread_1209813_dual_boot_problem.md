---
title: "dual boot problem"
date: 2009-07-10
forum: General Help
---

### Post by shva on 2009-07-10
I install both Ubuntu and Windows in my computer. I read some documentation, so I first install Windows XP on the last partition (instead of C disk as usual). And then I install Ubuntu on the other partitions. But when I turn on my computer, Windows is not in the boot list. I check /boot/grub/menu.lst, it looks:

[I]title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		3151677d-2419-4907-ad51-42a214bababe
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=3151677d-2419-4907-ad51-42a214bababe ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		3151677d-2419-4907-ad51-42a214bababe
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=3151677d-2419-4907-ad51-42a214bababe ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3151677d-2419-4907-ad51-42a214bababe
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3151677d-2419-4907-ad51-42a214bababe ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3151677d-2419-4907-ad51-42a214bababe
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3151677d-2419-4907-ad51-42a214bababe ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3151677d-2419-4907-ad51-42a214bababe
kernel		/boot/memtest86+.bin
quiet[/I]

So there is no Windows. How can I add Windows into the list? Thank you.

---

### Post by b166er on 2009-07-10
Try Adding this


title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
chainloader	+1


The same applies to Vista. the "title" is only a name.

---

### Post by merlinus on 2009-07-10
If that does not work, post results of:

```
sudo fdisk -l
```

---

### Post by shva on 2009-07-11
That doesn't work.. The result from sudo fdisk -l is:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2            3825       38912   281844360    f  W95 Ext'd (LBA)
/dev/sda5            3825        4334     4096543+  82  Linux swap / Solaris
/dev/sda6            4335        5609    10241406   83  Linux
/dev/sda7            5610       11983    51199123+  83  Linux
/dev/sda8           11984       24731   102398278+  83  Linux
/dev/sda9           24732       37479   102398278+  83  Linux
/dev/sda10          37480       38912    11510541    7  HPFS/NTFS


Thank you.


> **merlinus said:**
> If that does not work, post results of:

```
sudo fdisk -l
```

---

### Post by merlinus on 2009-07-11
Looks like windows is on sda10, which is a logical partition.  You will probably not get it to run, as it wants to be on a primary partition, usually the first on your hdd.

---

### Post by shva on 2009-07-11
Okay. So how should I do if I want to have windows in my computer too?

---

### Post by Finalfantasykid on 2009-07-11
Shouldn't you be able to edit the BOOT.ini file from your ubuntu partition?  I'm not sure which directory the boot.ini file is located though.  But if you edit that file(BECAREFUL with what you change!) you can change where you are booting from, in this case you would need to change which partition.

EDIT:  Here is a tutorial on how to edit [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022).  You probably just need to change the "...partition(9)" or maybe "...partition(10)"  I'm not sure whether it will start indexing at 0 or 1.

---

### Post by merlinus on 2009-07-11
You can try editing boot.ini, but as I said, windows wants to be on a primary, not logical, partition.

It seems that you have 4 linux partitions. 

```
df -h
```will show the mountpoints for each.

If you cannot get windows to run, then it would be a lengthy process to shrink and/or combine some of the linux partitions, and then shrink the extended partition to make space for a new primary one.

It might be best to back up important data and start fresh, installing windows first, and then linux.

---

