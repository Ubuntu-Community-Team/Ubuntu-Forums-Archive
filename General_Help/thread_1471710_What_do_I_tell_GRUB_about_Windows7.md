---
title: "What do I tell GRUB about Windows7?"
date: 2010-05-03
forum: General Help
---

### Post by xouns on 2010-05-03
I've fiddled around with my partitions today and I wrecked my GRUB in the process. I can boot Ubuntu, but my Win7 is unreachable. 
First situation: Triple boot, using WinXP(hd0,0), Ubuntu (hd0,4), swap (hd0,5), Win7 (hd0,1) and data (hd0,2). Everything worked, when I started up I would see GRUB 1.5, and for Windows I used a windows boot menu.

I removed the  WinXP partition, relocated Ubuntu to the first partition and resized the Win7 partition using Ubuntu 9.04 Live CD. My harddisk now looks like this (fdisk -l):
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3824    30716248+  83  Linux
/dev/sda2            3825        4461     5116702+  82  Linux swap / Solaris
/dev/sda3   *        4462       10198    46082452+   7  HPFS/NTFS
/dev/sda4           10199       60801   406468597+   7  HPFS/NTFS
```

So Ubuntu works fine now, Win7 booted for a moment, but (not having booted Ubuntu for a while) after updating the menu.lst, Win7 no longer works. I already tried to repair the boot via the Win7 CD, that fixed a few problems, but apparently not everything. Googleing around found that there are some chainloader things I might want to change, but that didn't seem to work (I'll post the GRUB error message in a bit).

```
update-grub Gives the following output:
gerbrand@gerbrand-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```
(Yes, it's and old install, but hey, that's what Linux is about, non?).

My menu.lst (last part) now looks like this:
```
## ## End Default Options ##

title		Ubuntu 9.10
uuid		2de6e843-f6a8-42e9-8774-e13a9a9b06e2
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=2de6e843-f6a8-42e9-8774-e13a9a9b06e2 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows
rootnoverify (hd0,2)
makeactive
chainloader +2
```

Suspecting the chainloader to be a problem, I've already tried chainloader +0 (seems to be a bad integer or something), chainloader, chainloader +1. All do not work. I vaguely remember that at some point this long, long, night, chainloader worked. 

Can somebody please point me in a direction, apart from reïnstalling, that may help me save my Win7 partition? I would greatly appreciate it. Thnx

---

### Post by xouns on 2010-05-03
Ah, never mind. I've used the Windows 7 disk again to repair the bootsector to the Windows drive (in the menu click Next, then repair). I have done this twice (the repair cycle) just to be sure.

Also, I have changed the menu.lst to read the following:
```
title		Windows 7
rootnoverify (hd0,2)
makeactive
chainloader +2

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		or maybe visit:
root

title		Ubuntu 9.10
uuid		2de6e843-f6a8-42e9-8774-e13a9a9b06e2
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=2de6e843-f6a8-42e9-8774-e13a9a9b06e2 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet
```
(Honoustly, at the moment of booting I have Ubuntu as the first, and Win7 as the second, but that shouldn't make a difference, right?).

So, for everybody else, this is what the Win7/ Ubuntu menu.lst should look like. It works, have fun.

---

### Post by oldfred on 2010-05-03
It should be chainloader +1  Does it work with +2??

If your windows entry is inside the automagic area it will get overwritten on the next kernel update. If you want it first you have to move it way up to above where it says begin automagic.

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=DarkRed]Here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

---

### Post by xouns on 2010-05-04
Ah, that explains why it disappeared after the last update. So, just for my understanding (I feel it is hard to get a good explanation of the menu.lst and the config files in general): the lines beginning with # are comments, right? Or do they work more like flags? And what can I and what can I not remove from the menu.lst?

What does the chainloader command do? Is it like a tag for the Windows-generated bootmenu? Chainloader +2 works very well, I don't know if chainloader +1 works, won't be home for a couple of days.

---

### Post by oldfred on 2010-05-04
Chainloader just tells it to jump to a location and continue booting. I thought the +1 meant to the first sector in the partition, but do not know for sure.

---

