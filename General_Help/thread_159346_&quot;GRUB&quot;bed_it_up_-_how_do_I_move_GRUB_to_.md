---
title: "&quot;GRUB&quot;bed it up - how do I move GRUB to a different drive"
date: 2006-04-12
forum: General Help
---

### Post by Cuppa-Chino on 2006-04-12
Hi,

I have system with IDE hd (hda) and a SATA hd (sda) - I am now replacing the IDE drive with another SATA drive (will be sdb) - when installing Ubuntu I could never get GRUB onto sda - so it landed on hda. Now hda is going to disappear I need to move it sda (or sdb), I tried just installing GRUB onto SDA it gets to the menu but then fails: the mappings do not work for Linux anymore and for windows it says something like "NT Loader not present".
Any help would be much appreciated

Thanks

PS Needless to say no operating system was on hda.

PPS

Grub Menu looks like this```
title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-686-smp
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

and Device map like this
```
(hd0)	/dev/hda
(hd1)	/dev/sda

```

will I need to override the device map when I unplug hda?

---

### Post by DOtSlaSHuCantCME on 2006-04-12
This is from a GruB restore guide.


1. pop in the live cd, boot from it until you reach the desktop
2.open a terminal window .
3.type"grub"
4.type "root (hd0,6)" ,or whatever your harddisk +boot partition numbers are.
5.type"setup" (hd0)" ,or whatever your harddisk nr is
6.Quit grub by typing "quit".
7.reboot.

Heres another way  ,you choose whether to install to linux root,or xp mbr
or to another drive.

1.Boot from live cd like knoppix,mepis,ubuntu or similar.

2.Open a terminal,go superuser(type su)enter root pass as necessary.

3.Type "grub" ,which makes a grumb prompt appear.

4.Type "find /boot/grub/stage1. youll get an response like "(hd0)" or in my case (hd0,3),use whatever your computer spitts out for the next lines.

5.Type "root (hd0,3).

6.Type "setup (hd0,3)", **other instructions says to use "(hd0) ,and thats fine if u want to write GRUB to the mbr. if you want to write it to your linux root partition, then you want the number after the comma,such as "(hd0,3).**

7.Type "quit".

8.REBOOT.....(remove cd).
  


:cool:  Got  the above proven method(s) from this community.





title		Ubuntu, kernel 2.6.12-10-686-smp 
root		**(hd1,2)**
kernel		/boot/vmlinuz-2.6.12-10-686-smp** root=/dev/sda3 ro quiet splash**
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

Had to reread your post,did you Try the grub install with a live cd?

---

### Post by Cuppa-Chino on 2006-04-15
Did try it exactly as you suggested... no luck so far...

my partition structure looks like this:

**SDA (sata drive 1 - on first sata port)**
[LIST]
[*]Primary NTFS Partition - Windows "C:\" 
[*]Logical Partition - with 2 NTFS, 1 FAT & Linux Swap (in that order)
[*]Primary Ext3 Partition with Ubuntu Root
[*]Primary Ext3 Partition for other Linuxes
[/LIST]
**SDB (2nd sata drive)**
[LIST]
[*]Primary NTFS Partition
[*]Logical Partition with 1 NTFS
[/LIST]

Ideally I would like to have Grub running as such as that 
[LIST=1]
[*]usually boot mode is into Grub menu
[*]that I can use Bios to choose other HD as boot HD this then boots straight into Windows
[/LIST]

I currently boot from SDA - it goes straight into Windows - I guess need to install Grub onto SDB - what I mean here is tell MBR (?) on SDB to load Grub.

;) 

[SIZE="4"][COLOR="Navy"]**_Thanks for all your help!_**[/COLOR][/SIZE]

---

