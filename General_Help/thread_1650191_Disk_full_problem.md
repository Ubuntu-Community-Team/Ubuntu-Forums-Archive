---
title: "Disk full problem"
date: 2010-12-21
forum: General Help
---

### Post by fenrith on 2010-12-21
Hi all.

I'm having a problem with my dual-boot XP/Ubuntu 10.04 system. The Ubuntu partition is clearly too small (that's another issue) at approximately 7.7Gb, even though I keep most of my data on the shared NTFS drive. At the moment, when I carry out a df, it shows 99% usage, with just over 100Mb available. According to the disk usage analyzer, 3.7Gb are used in the /home folder. However, some 90% of that space is unaccounted for: the largest folder within /home is 104.6 Mb, and the total of all directories comes to under 360 Mb.

What is taking up the rest of the space, and how can I free it up?
The results of df:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              7689788   7195672    103492  99% /
none                   1022504       300   1022204   1% /dev
none                   1026724      5372   1021352   1% /dev/shm
none                   1026724       308   1026416   1% /var/run
none                   1026724         0   1026724   0% /var/lock
none                   1026724         0   1026724   0% /lib/init/rw
/dev/sda1            100049008  94582432   5466576  95% /media/Windrive_
/dev/sda3              7152636   3283940   3868696  46% /media/Shared
/dev/sda4              1627132    248428   1378704  16% /media/OS_TOOLS


Results of sudo fdisk -l:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a910a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12456   100049008+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           12456       13500     8389457+   f  W95 Ext'd (LBA)
/dev/sda3           13501       14391     7152640    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           14391       14594     1627136    7  HPFS/NTFS
/dev/sda5           12456       13429     7812500   83  Linux
/dev/sda6           13429       13500      576512   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)


---

### Post by Dave_L on 2010-12-21
Disk Usage Analyzer is a convenient way to see what's taking up the space.

If it's not in the menu, it can be run from the Ubuntu command shell:

```
$ baobab &
```

It's part of the package gnome-utils.

---

### Post by Verbeck on 2010-12-21
could you post a screenshot of the disk usage analyser after scanning your home folder?

---

### Post by iiiears on 2010-12-21
Hello,

A few things to check out.

1.) Is the trash empty? - Right click on the Trash icon it's on the lower taskbar.

2.) Updating your system keeps dl'ed packages in /var/cache/apt/archives
for quick reinstallation. You can change that 
Synaptic Package Manager> Settings > Preferences > Files - Select the best option for you. _OR_ move the .deb files to another disk and restore them if you like to "sudo nautilus /var/cache/apt/archives" if you really need them. An external USB drive is very handy for this. 

3.) Unhide files in your /home/UserName Directory with Ctrl+H and poke around a bit. Self installed Fonts, are my weakness and windows games store their data there and use a large amount of disk space.

4.) If you are feeling adventurous you can use gparted to resize things as you want them. those utilitie are free of course. though it will take a couple of hours to do.

   Best wishes.

---

### Post by fenrith on 2010-12-21
ADave_L, @Verbeck, thanks for all the suggestions. It turns out @iiears had the answer - when looking through the hidden files I located a 3.3 Gb log file that had been constructed by testdisk whilst I was trying to rescue a damaged hard drive. Log deleted, problem solved.:)

Thanks all.

---

