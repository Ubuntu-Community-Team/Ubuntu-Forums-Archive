---
title: "Computer keeps shutting down"
date: 2012-01-16
forum: General Help
---

### Post by jacobgerber on 2012-01-16
Hello all,
I recently installed Ubuntu 11.10 as a dual boot with Windows XP on an old Dell Dimension E510 computer. I partitioned the hard drive as best I could from tutorials I could find on the internet, but I think that I might have done something wrong, because the computer shuts down without warning often--both when I am running Windows and when I am running Ubuntu.

My wife saw an error message "NTFS volume is dirty" at one point, and here is the result from running fdisk -l in my terminal:

********************************

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       96389       48163+  de  Dell Utility
/dev/sdb2   *       96390   227785634   113844622+   7  HPFS/NTFS/exFAT
/dev/sdb3       227788798   305876991    39044097    5  Extended
/dev/sdb4       305877600   312480314     3301357+  db  CP/M / CTOS / ...
/dev/sdb5       227788800   244566015     8388608   83  Linux
/dev/sdb6       244568064   261345279     8388608   82  Linux swap / Solaris
/dev/sdb7       261347328   305876991    22264832   83  Linux

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   227785634   113844622+   7  HPFS/NTFS/exFAT
/dev/sda3       227788798   305876991    39044097    5  Extended
/dev/sda4       305877600   312480314     3301357+  db  CP/M / CTOS / ...
/dev/sda5       227788800   244566015     8388608   83  Linux
/dev/sda6       244568064   261345279     8388608   82  Linux swap / Solaris
/dev/sda7       261347328   305876991    22264832   83  Linux

Disk /dev/mapper/isw_cjafcahegg_ARRAY: 160.0 GB, 159996968960 bytes
255 heads, 63 sectors/track, 19451 cylinders, total 312494080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

                           Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cjafcahegg_ARRAY1              63       96389       48163+  de  Dell Utility
/dev/mapper/isw_cjafcahegg_ARRAY2   *       96390   227785634   113844622+   7  HPFS/NTFS/exFAT
/dev/mapper/isw_cjafcahegg_ARRAY3       227788798   305876991    39044097    5  Extended
/dev/mapper/isw_cjafcahegg_ARRAY4       305877600   312480314     3301357+  db  CP/M / CTOS / ...
/dev/mapper/isw_cjafcahegg_ARRAY5       227788800   244566015     8388608   83  Linux
/dev/mapper/isw_cjafcahegg_ARRAY6       244568064   261345279     8388608   82  Linux swap / Solaris
/dev/mapper/isw_cjafcahegg_ARRAY7       261347328   305876991    22264832   83  Linux

Disk /dev/mapper/isw_cjafcahegg_ARRAY1: 49 MB, 49319424 bytes
255 heads, 63 sectors/track, 5 cylinders, total 96327 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x481ec400

This doesn't look like a partition table
Probably you selected the wrong device.

                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cjafcahegg_ARRAY1p1   ?     4720257   113051776    54165760   ff  BBT
/dev/mapper/isw_cjafcahegg_ARRAY1p2   ?   543912809  2413684173   934885682+   0  Empty
/dev/mapper/isw_cjafcahegg_ARRAY1p3   ?     7497060  1287563943   640033442   20  Unknown
/dev/mapper/isw_cjafcahegg_ARRAY1p4   ?           0           0           0   42  SFS

Partition table entries are not in disk order

Disk /dev/mapper/isw_cjafcahegg_ARRAY2: 116.6 GB, 116576893440 bytes
255 heads, 63 sectors/track, 14173 cylinders, total 227689245 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cjafcahegg_ARRAY2p1   ?   218129509  1920119918   850995205   72  Unknown
/dev/mapper/isw_cjafcahegg_ARRAY2p2   ?   729050177  1273024900   271987362   74  Unknown
/dev/mapper/isw_cjafcahegg_ARRAY2p3   ?   168653938   168653938           0   65  Novell Netware 386
/dev/mapper/isw_cjafcahegg_ARRAY2p4      2692939776  2692991410       25817+   0  Empty

Partition table entries are not in disk order

Disk /dev/mapper/isw_cjafcahegg_ARRAY4: 3380 MB, 3380590080 bytes
255 heads, 63 sectors/track, 411 cylinders, total 6602715 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cjafcahegg_ARRAY4p1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/mapper/isw_cjafcahegg_ARRAY4p2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/mapper/isw_cjafcahegg_ARRAY4p3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/mapper/isw_cjafcahegg_ARRAY4p4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order

Disk /dev/mapper/isw_cjafcahegg_ARRAY5: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cjafcahegg_ARRAY5 doesn't contain a valid partition table

Disk /dev/mapper/isw_cjafcahegg_ARRAY6: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cjafcahegg_ARRAY6 doesn't contain a valid partition table

Disk /dev/mapper/isw_cjafcahegg_ARRAY7: 22.8 GB, 22799187968 bytes
255 heads, 63 sectors/track, 2771 cylinders, total 44529664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cjafcahegg_ARRAY7 doesn't contain a valid partition table

********************************

I really enjoy using Linux, but I'm really over my head here. Any thoughts about how to fix this?

Also, I don't really have any files saved on Linux outside of my Dropbox folder, so if I need to reinstall Ubuntu and start over, that's not a problem.

Thank you so much for any help you can offer!

Jacob

---

### Post by jerrrys on 2012-01-17
This may help

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=testdisk&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=testdisk&sa=Search&cof=FORID:9)

---

### Post by imachavel on 2012-01-17
test disk doesn't sound bad. but I would use boot repair disk myself. It helped me, when my grub was gone. Now you look like you have quite a few partitions, how many OS'es? looks like you have 3 OSes and swap space. I'm guessing you didn't install linux 'along side' but actually partitioned and formatted the disk then installed each OS right? try boot repair, if it doesn't work, then simply try the 'save boot log' option as I believe it says instead of 'repair boot'

then remember where the log is saved, and up load it in a thread. this as far as I know, because I had the same issue recently, and had to use boot repair. Boot repair fixed it, thanks for members who are ubuntu caffienated ubunters hahah
btw how much ram you got in that dell??

[http://reviews.cnet.com/desktops/dell-dimension-e510-pentium/1707-3118_7-31555136.html](http://reviews.cnet.com/desktops/dell-dimension-e510-pentium/1707-3118_7-31555136.html)

---

### Post by jacobgerber on 2012-01-24
Thank you for the above suggestions. I tried them both, but then I discovered that I have a hard drive that utilizes FakeRaid, and I read [here]("https://wiki.ubuntu.com/Raid") that Linux just doesn't work well on that kind of a system. So, I decided instead to log into Windows, delete the partition with Linux installed, but when I was just about to work on fixing the boot record, the computer shut down my me again.

Now the computer comes up with "Grub Rescue Error" when I restart. I have found several people suggesting that I just need the Windows XP installation CD to fix the master boot record (one article [here]("http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/")), but when I tried that, the computer told me that it couldn't find a valid hard drive installed. (!)

Any suggestions here? I would appreciate any help on figuring out what I might have done (and how I might fix it) for the computer not to be able to find a hard drive. By the way, when I boot up, the computer lists the hard drive(s) on the screen right before it gets to "Grub Rescue Error" if that helps.

Thanks!

---

