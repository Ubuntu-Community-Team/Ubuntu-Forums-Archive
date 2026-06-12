---
title: "Boot MS-DOS with Grub"
date: 2006-03-12
forum: General Help
---

### Post by duralisis on 2006-03-12
Here's my setup, I have 3 hard drives installed and a cd-rw.  Ubuntu is installed on the second drive and the boot loader is installed to the MBR of the Windows partition.

```
hda1	ntfs	windowsxp
hdb1	ext3	/
hdb5	swap	/swap
hdc1	fat	msdos (c:)
hdc5	fat	msdos (d:)
```

hdc is the master on the secondary ide chain with the cd-rw, and DOS was installed while it was the only drive in the system (partitioned into two drives for fat16).

*What I want to do* is add a grub menu entry to boot my DOS partition as well, but when I do, I get "System disk error" (or something similar) and it loops back to the grub menu!

Here's my abbreviated menu.lst so far:

```
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

...

title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# MS-DOS Partition on /dev/hdc1
title		MS-DOS 6.22
root		(hd2,0)
savedefault
makeactivve
chainloader	+1
```

I've also tried:

```
title		MS-DOS 6.22
rootnoverify	(hd2,0)
chainloader	+1
```

... but it seems to have no effect.

So, what am I missing? Help me, grub experts! :)

---

### Post by nanotube on 2006-03-12
i am not a grub expert my any means... but i noticed you have a misspelling in your msdos section, you have "makeactivve" with two v's. maybe correcting that will make a difference?

---

### Post by duralisis on 2006-03-12
Didn't notice that :eek:.

But I also tried the second entry which doesn't have makeactive and it turns up the same results.  I was looking up grub usage in various places and I found a "hide/unhide" command used in large multiboot configurations, but I don't know how to use it or apply it to this.

---

### Post by lha on 2006-03-12
Hide/unhide trickery is needed only when booting from a partition that is not the first primary partition visible to DOS. Try

```
# MS-DOS Partition on /dev/hdc1
title		MS-DOS 6.22
root		(hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader	+1
```

---

### Post by dcstar on 2006-03-12
[QUOTE=lha]Hide/unhide trickery is needed only when booting from a partition that is not the first primary partition visible to DOS. Try

```
# MS-DOS Partition on /dev/hdc1
title		MS-DOS 6.22
root		(hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader	+1
```[/QUOTE]
Or if that doesn't work, maybe:

```
# MS-DOS Partition on /dev/hdc1
title		MS-DOS 6.22
root		(hd2,0)
hide		(hd0,0)
hide		(hd1,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader	+1
```

---

### Post by duralisis on 2006-03-12
The first entry without hiding works great, no problems at all.  But after trying the second one, I was able to boot to DOS once, then after restarting GRUB gives me an "Error 17" message!

I'm going to try the live cd and see if I can modify the menu or get it working again.

---

### Post by dcstar on 2006-03-12
[QUOTE=duralisis]The first entry without hiding works great, no problems at all.  But after trying the second one, I was able to boot to DOS once, then after restarting GRUB gives me an "Error 17" message!

I'm going to try the live cd and see if I can modify the menu or get it working again.[/QUOTE]
Just "unhide" the partitions so Grub can use them again - I think you can do this with various utilities (and don't use the "hide" options if they cause problems!!)

[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

---

### Post by lha on 2006-03-12
[QUOTE=duralisis]The first entry without hiding works great, no problems at all.  But after trying the second one, I was able to boot to DOS once, then after restarting GRUB gives me an "Error 17" message!

I'm going to try the live cd and see if I can modify the menu or get it working again.[/QUOTE]

No wonder. 'hide (hd1,0)' turned your Ubuntu partition into [amoeba]("http://www.cs.vu.nl/pub/amoeba/amoeba.html"). You shouldn't use hide to manipulate Linux partitions. The good news is, contents are (likely to be) intact and you just need to change the partition label back linux. Boot with a live cd and use fdisk to change hdb1's type to 83. Command 't' does the trick. (Type a letter 't' and press enter) Fdisk asks for partition number and then for the new (and correct) label.

---

### Post by duralisis on 2006-03-12
A-ha! Solved; thanks lha.  Fdisk fixed it and everything boots just fine now; I just have to get rid of that one entry.  I also changed 'hda1' back to regular type 7 ntfs.  Since it was hidden it got set to 17 (hidden ntfs).

---

### Post by dcstar on 2006-03-13
[QUOTE=lha]No wonder. 'hide (hd1,0)' turned your Ubuntu partition into [amoeba]("http://www.cs.vu.nl/pub/amoeba/amoeba.html"). You shouldn't use hide to manipulate Linux partitions. The good news is, contents are (likely to be) intact and you just need to change the partition label back linux. Boot with a live cd and use fdisk to change hdb1's type to 83. Command 't' does the trick. (Type a letter 't' and press enter) Fdisk asks for partition number and then for the new (and correct) label.[/QUOTE]
When I read the Grub info it said that booting DOS could be problematical if there were filesystems on drives in front of it, so it had those hide commands as the solution.

Apologies to duralisis for causing him problems!

---

### Post by DaBruGo on 2006-03-14
duralisis,

I don't know if this will help, but I have no problems booting XP from my menu.lst file. You should be able to modify the menu command from this [LINK]("http://www.ubuntuforums.org/showpost.php?p=441318&postcount=2") to get DOS booting as well.

Just make sure that you place any Windows or DOS menu options either above or below the automagic kernel section in menu.lst or they will get changed whenever you do a kernel update. Here is a [LINK]("http://www.ubuntuforums.org/showpost.php?p=774688&postcount=12") explaining that for you.

Hope that helps.


DAVE

---

