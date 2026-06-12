---
title: "format usb stick udf to ntfs"
date: 2011-07-06
forum: General Help
---

### Post by rudedcam on 2011-07-06
i have a usb stick divided in two; a partition of NTFS for the most part and a small annoying part of a few Mb in UDF which mounts every time as a cdrom.

how do i get rid of the small UDF part?

I have tried to format everything as one big chunk in NTFS with Gparted without success. 
I have also tried something i found on the net under windows:
1.click Start>>run>> type "CMD">> enter
2.type format X: /FS:NTFS (X would be the drive letter)
but it won't let me format the UDF part.

thanks a lot in advance

---

### Post by ajgreeny on 2011-07-06
Try ```
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1 && sudo partprobe /dev/sdX
``` [COLOR=Red]CAUTION:-[/COLOR]
Make sure you get the sdX correct for your usb stick or you could wipe your main install.  That command will wipe everything on the disk and put zeros in its place, thereby returning the disk to a virgin unpartitioned state, from where gparted should be able to handle it, and make new partitions.

---

### Post by nzjethro on 2011-07-06
Rudedcam, can you delete both of the partitions, either in GParted or Windows Disk Management? If so, do that, and create a new partition tabel with just a single ntfs partition. If not, what error messages occur?

---

### Post by coffeecat on 2011-07-06
> **rudedcam said:**
> i have a usb stick divided in two; a partition of NTFS for the most part and a small annoying part of a few Mb in UDF which mounts every time as a cdrom.

how do i get rid of the small UDF part?

Is that a flash drive? Because, if so, I doubt that the UDF bit is part of the actual flash drive and may be a separate read-only device within the stick. My reason? Windows treats USB flash drives as if they were superfloppies and will only mount the first partition. Since most customers for that device will be using Windows, it wouldn't be much use to them if only the UDF part were mounted in Windows. Unless the manufacturer has done something really clever to fool Windows into thinking there are two devices there.

Whatever, before you run any dd commands or try to re-format the drive, run this command to see what is there - and post the output:

```
sudo fdisk -lu
```

**EDIT**: Just remembered. The very first USB flash drive I bought did have some sort of separate partition, but was usable in Windows. So there must be a way of fooling Windows because Windows will only mount the first partition if you make conventional partitions on a pendrive. Anyway - the output of fdisk would still be useful.

---

### Post by rudedcam on 2011-07-06
wonderful! this is getting interesting!
it is a usb flash drive (actually a have a few) made for a pharmaceutic company as promotional gifts. when plugged in, a part of it with their annoying advertisement is mounted as a cdrom and the rest as an external device.

ajgreeny, i've tried the codes and it wiped the stick (which was easily reformatted with gparted)... but the UDF part remains. 

gparted sees it as one partition of 1.85 out of 2Go.

```
****@*****:~$ sudo dd if=/dev/zero of=/dev/sdc bs=512 count=1 && sudo partprobe /dev/sdc
[sudo] password for rudecam: 
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000619422 s, 827 kB/s


****@*****:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf5acf27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3        30812670   338007599   153597465    7  HPFS/NTFS
/dev/sda4       338007600   976768064   319380232+   5  Extended
/dev/sda5       338007663   358490474    10241406   82  Linux swap / Solaris
/dev/sda6       358490538   976768064   309138763+  83  Linux

Disk /dev/sdc: 1987 MB, 1987575808 bytes
255 heads, 63 sectors/track, 241 cylinders, total 3881984 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000dce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     3871664     1935801   83  Linux

```

> I doubt that the UDF bit is part of the actual flash drive and may be a separate read-only device within the stick.
so, humm, maybe you are right coffeecat; in that case, would it be possible to destroy/disable that read-only device?

thanks for all the thoughts guys, i find it stimulating for the mind

---

### Post by coffeecat on 2011-07-07
> **rudedcam said:**
> in that case, would it be possible to destroy/disable that read-only device?

thanks for all the thoughts guys, i find it stimulating for the mind

The fdisk output is interesting. Particularly after you ran ajgreeny's dd command. The dd would have zeroed out the partition table. Did you re-create a partition table and create a partition after running dd? Because there must have been a partition table on your flash drive when you ran fdisk.

It is seen as a 1987MB drive, but there's an interesting gap at the end. The end sector of the drive is 3881984, but the end sector of the one sdc1 partition is 3871664, which is a difference of 10320 sectors = 5.2MB. That's a big seemingly unused gap - I wonder if the UDF stuff is sitting in there and some whizzy firmware in the drive is presenting this as a CDROM. Which is perhaps how it could get round the Windows limitation.

Try zeroing the whole drive. Use:

```
sudo shred -vzn 0 /dev/sdc
```

**Please** double-check that the flash drive is being seen as sdc before you start. You don't want to zero the wrong drive! Once it has been completely zeroed, use Gparted or Disk Utility to create a new partition table and partition and then see what happens. I'll await developments with interest.

---

### Post by rudedcam on 2011-07-07
> Did you re-create a partition table and create a partition after running dd? Because there must have been a partition table on your flash drive when you ran fdisk.
yes i did format to EXT2, sorry, i forgot to mention it.
```
***@****:~$ sudo fdisk -lu
[sudo] password for rudecam: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf5acf27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3        30812670   338007599   153597465    7  HPFS/NTFS
/dev/sda4       338007600   976768064   319380232+   5  Extended
/dev/sda5       338007663   358490474    10241406   82  Linux swap / Solaris
/dev/sda6       358490538   976768064   309138763+  83  Linux

Disk /dev/sdc: 1987 MB, 1987575808 bytes
255 heads, 63 sectors/track, 241 cylinders, total 3881984 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000dce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     3871664     1935801   83  Linux
***@***:~$ sudo shred -vzn 0 /dev/sdc
shred: /dev/sdc: pass 1/1 (000000)...
shred: /dev/sdc: pass 1/1 (000000)...75MiB/1.9GiB 3%
shred: /dev/sdc: pass 1/1 (000000)...76MiB/1.9GiB 4%
shred: /dev/sdc: pass 1/1 (000000)...158MiB/1.9GiB 8%
shred: /dev/sdc: pass 1/1 (000000)...159MiB/1.9GiB 8%
shred: /dev/sdc: pass 1/1 (000000)...241MiB/1.9GiB 12%
shred: /dev/sdc: pass 1/1 (000000)...242MiB/1.9GiB 12%
shred: /dev/sdc: pass 1/1 (000000)...327MiB/1.9GiB 17%
shred: /dev/sdc: pass 1/1 (000000)...328MiB/1.9GiB 17%
shred: /dev/sdc: pass 1/1 (000000)...419MiB/1.9GiB 22%
shred: /dev/sdc: pass 1/1 (000000)...420MiB/1.9GiB 22%
shred: /dev/sdc: pass 1/1 (000000)...515MiB/1.9GiB 27%
shred: /dev/sdc: pass 1/1 (000000)...516MiB/1.9GiB 27%
shred: /dev/sdc: pass 1/1 (000000)...615MiB/1.9GiB 32%
shred: /dev/sdc: pass 1/1 (000000)...616MiB/1.9GiB 32%
shred: /dev/sdc: pass 1/1 (000000)...719MiB/1.9GiB 37%
shred: /dev/sdc: pass 1/1 (000000)...720MiB/1.9GiB 37%
shred: /dev/sdc: pass 1/1 (000000)...814MiB/1.9GiB 42%
shred: /dev/sdc: pass 1/1 (000000)...815MiB/1.9GiB 42%
shred: /dev/sdc: pass 1/1 (000000)...918MiB/1.9GiB 48%
shred: /dev/sdc: pass 1/1 (000000)...919MiB/1.9GiB 48%
shred: /dev/sdc: pass 1/1 (000000)...1022MiB/1.9GiB 53%
shred: /dev/sdc: pass 1/1 (000000)...1023MiB/1.9GiB 53%
shred: /dev/sdc: pass 1/1 (000000)...1.0GiB/1.9GiB 59%
shred: /dev/sdc: pass 1/1 (000000)...1.1GiB/1.9GiB 59%
shred: /dev/sdc: pass 1/1 (000000)...1.2GiB/1.9GiB 64%
shred: /dev/sdc: pass 1/1 (000000)...1.3GiB/1.9GiB 70%
shred: /dev/sdc: pass 1/1 (000000)...1.4GiB/1.9GiB 75%
shred: /dev/sdc: pass 1/1 (000000)...1.5GiB/1.9GiB 81%
shred: /dev/sdc: pass 1/1 (000000)...1.6GiB/1.9GiB 86%
shred: /dev/sdc: pass 1/1 (000000)...1.7GiB/1.9GiB 91%
shred: /dev/sdc: pass 1/1 (000000)...1.8GiB/1.9GiB 97%
shred: /dev/sdc: pass 1/1 (000000)...1.9GiB/1.9GiB 100%
***@***:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf5acf27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3        30812670   338007599   153597465    7  HPFS/NTFS
/dev/sda4       338007600   976768064   319380232+   5  Extended
/dev/sda5       338007663   358490474    10241406   82  Linux swap / Solaris
/dev/sda6       358490538   976768064   309138763+  83  Linux

Disk /dev/sdc: 1987 MB, 1987575808 bytes
62 heads, 62 sectors/track, 1009 cylinders, total 3881984 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
***@***:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf5acf27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3        30812670   338007599   153597465    7  HPFS/NTFS
/dev/sda4       338007600   976768064   319380232+   5  Extended
/dev/sda5       338007663   358490474    10241406   82  Linux swap / Solaris
/dev/sda6       358490538   976768064   309138763+  83  Linux

Disk /dev/sdc: 1987 MB, 1987575808 bytes
255 heads, 63 sectors/track, 241 cylinders, total 3881984 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4e8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     3871664     1935801   83  Linux

```
pretty impressive uh?

any other ideas before I give up? ;)

---

### Post by coffeecat on 2011-07-08
> **rudedcam said:**
> pretty impressive uh?

:)

After completely zeroing the flash drive, you had a zeroed partition table:

```
Disk /dev/sdc: 1987 MB, 1987575808 bytes
62 heads, 62 sectors/track, 1009 cylinders, total 3881984 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: [COLOR=Red]0x00000000[/COLOR]

Disk /dev/sdc doesn't contain a valid partition table
```Which is good. But then after reformatting it, you still get that 5.3MB gap at the end.

```
Disk /dev/sdc: 1987 MB, 1987575808 bytes
255 heads, 63 sectors/track, 241 cylinders, total [COLOR=Red]3881984 [/COLOR]sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4e8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     [COLOR=Red]3871664[/COLOR]     1935801   83  Linux
```Which is most curious. You don't say, but I presume after all that you are still getting the pseudo-CDROM? If so, I do have no further ideas. Sorry. There must be something in the firmware. If it's promotional stuff, I guess they've gone to some lengths to make sure it's not erasable. Pharmaceutical companies have deep pockets and take their promotional material very seriously! :p

**EDIT**: I have just had an idea! :idea:

You could use sfdisk to edit the partition table directly to create a small extra partition in that 5.3 MB space, and then zero the extra partition only. My theory is that the firmware is reserving that space to write the UDF stuff or to use as a cache. If the former, it might work. If the latter, then it will just get overwritten again by the firmware and the pseudo-CDROM will reappear. I have a feeling in my bones that this may not work, but if you want help with the sfdisk bit, post back. I'm willing to give it a try - this has quite intrigued me.

If you do want to try it, plug the USB drive in, and:

```
sudo sfdisk -d /dev/sdc > Desktop/flashparts.txt
```

And then post the contents of flashparts.txt which will have appeared on your desktop.

---

### Post by rudedcam on 2011-07-08
> Which is most curious. You don't say, but I presume after all that you are still getting the pseudo-CDROM? If so, I do have no further ideas. Sorry. There must be something in the firmware. If it's promotional stuff, I guess they've gone to some lengths to make sure it's not erasable. Pharmaceutical companies have deep pockets and take their promotional material very seriously! 
i am also trilled and i enjoy the learning of dd and shred commands.
as you said, pharmaceutical companies probably don't want me to wipe their promo ;)

```
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=  3871602, Id=83
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
```
what does this mean to you? anything we can do?

gotta spend some time with my girlfriend now, enough geeking for today she said! :D

---

### Post by coffeecat on 2011-07-09
Your output of sfdisk is exactly what is needed, and it does mean something to me. :wink: I shall post back with some detailed instructions in a few hours when I have more time.

---

### Post by coffeecat on 2011-07-10
Sorry for the delay – long day yesterday, and wanted to get this right. I'm not overly optimistic that this is going to work because I think the flashdrive firmware may be reserving or rewriting, or even preventing writing to the last 5MB or so of the drive, but let's have a try anyway.

First – a precaution. Backup the partition table on your main drive. Why? One single typo later on and you overwrite the partition table on your main drive with the edited flashdrive one. I know you won't but let's get that sda drive partition table backed up anyway. You never know when you might need it.

```
sudo sfdisk -d /dev/sda > Desktop/PTsda.txt
```

Save the Ptsda.txt file in your archives and/or backup media. Now you can turn your attention to the flash drive. First, plug the flash drive in and:

```
sudo fdisk -lu
```

Double-check that it is still being seen as sdc. I am intrigued that there is no sdb listed. Do you have a card reader in that machine? If the flashdrive is still sdc, then save this following text as flashparts_edited.txt on your desktop (copy and paste it into gedit):

```
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=  3871602, Id=83
/dev/sdc2 : start=  3871665, size=    10318, Id=83
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
```

Now force write it to your flash drive with:

```
sudo sfdisk --force /dev/sdc < Desktop/flashparts_edited.txt
```

Now unmount the flash drive (its first partition), remove it, wait a few seconds and plug it back in again. Run this again:

```
sudo fdisk -lu
```

Does this show both sdc1 and sdc2, or sdc1 only? If sdc1 only, post back. If both, proceed. If this has worked so far, you will have a second partition covering that approx 5MB at the end. It won't have a filesystem, but that doesn't matter. Now:

```
sudo shred -vzn 0 /dev/sdc2
```

That will zero only inside the sdc2 partition you've just made, including the udf stuff if my theory is correct, leaving the larger sdc1 intact. Remove the flash drive and plug it in again. What happens? Is the pseudo-CDROM still there?

**HEALTH WARNING**. I have double-checked my post and I don't think I've made a mistake, but double-check that the flash drive is still sdc and that my posted commands (except the first one) refer to sdc . Be very, **very** careful when typing. I managed to zero out the partition table on my main sda drive once, through one careless typo. That is not a mistake you will want to make, nor I to repeat. :(

---

### Post by rudedcam on 2011-07-14
sorry for my delay, one of those school rush...

well.... it was such a constructive learning experience for me. the pharmaceutical company wins :( i still get that advertising crap!
```
***@***:~$ sudo sfdisk -d /dev/sda > Desktop/PTsda.txt

[sudo] password for ***: 

***@***:~$ sudo fdisk -lu



Disk /dev/sda: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0xcf5acf27



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1              63       80324       40131   de  Dell Utility

/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS

/dev/sda3        30812670   338007599   153597465    7  HPFS/NTFS

/dev/sda4       338007600   976768064   319380232+   5  Extended

/dev/sda5       338007663   358490474    10241406   82  Linux swap / Solaris

/dev/sda6       358490538   976768064   309138763+  83  Linux

***@***:~$ sudo fdisk -lu



Disk /dev/sda: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0xcf5acf27



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1              63       80324       40131   de  Dell Utility

/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS

/dev/sda3        30812670   338007599   153597465    7  HPFS/NTFS

/dev/sda4       338007600   976768064   319380232+   5  Extended

/dev/sda5       338007663   358490474    10241406   82  Linux swap / Solaris

/dev/sda6       358490538   976768064   309138763+  83  Linux



Disk /dev/sdc: 1987 MB, 1987575808 bytes

255 heads, 63 sectors/track, 241 cylinders, total 3881984 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x0002d0df



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1              63     3871664     1935801   83  Linux

***@***:~$ sudo sfdisk -d /dev/sda > Desktop/PTsda.txt

***@***:~$ sudo sfdisk --force /dev/sdc < Desktop/flashparts_edited.txt

Checking that no-one is using this disk right now ...

BLKRRPART: Device or resource busy



This disk is currently in use - repartitioning is probably a bad idea.

Umount all file systems, and swapoff all swap partitions on this disk.

Use the --no-reread flag to suppress this check.



Disk /dev/sdc: 241 cylinders, 255 heads, 63 sectors/track

Old situation:

Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0



   Device Boot Start     End   #cyls    #blocks   Id  System

/dev/sdc1          0+    240     241-   1935801   83  Linux

/dev/sdc2          0       -       0          0    0  Empty

/dev/sdc3          0       -       0          0    0  Empty

/dev/sdc4          0       -       0          0    0  Empty

Warning: given size (10318) exceeds max allowable size (0)

New situation:

Units = sectors of 512 bytes, counting from 0



   Device Boot    Start       End   #sectors  Id  System

/dev/sdc1            63   3871664    3871602  83  Linux

/dev/sdc2       3871665   3881982      10318  83  Linux

/dev/sdc3             0         -          0   0  Empty

/dev/sdc4             0         -          0   0  Empty

Warning: partition 2 extends past end of disk

Successfully wrote the new partition table



Re-reading the partition table ...

BLKRRPART: Device or resource busy

The command to re-read the partition table failed

Reboot your system now, before using mkfs



If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)

to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1

(See fdisk(8).)

***@***:~$ sudo fdisk -lu

[sudo] password for ***: 



Disk /dev/sda: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0xcf5acf27



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1              63       80324       40131   de  Dell Utility

/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS

/dev/sda3        30812670   338007599   153597465    7  HPFS/NTFS

/dev/sda4       338007600   976768064   319380232+   5  Extended

/dev/sda5       338007663   358490474    10241406   82  Linux swap / Solaris

/dev/sda6       358490538   976768064   309138763+  83  Linux



Disk /dev/sdc: 1987 MB, 1987575808 bytes

62 heads, 62 sectors/track, 1009 cylinders, total 3881984 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x0002d0df



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1              63     3871664     1935801   83  Linux

Partition 1 has different physical/logical beginnings (non-Linux?):

     phys=(0, 1, 1) logical=(0, 1, 2)

Partition 1 has different physical/logical endings:

     phys=(240, 254, 63) logical=(1007, 12, 13)

Partition 1 does not end on cylinder boundary.

/dev/sdc2         3871665     3881982        5159   83  Linux

Partition 2 has different physical/logical beginnings (non-Linux?):

     phys=(241, 0, 1) logical=(1007, 12, 14)

Partition 2 has different physical/logical endings:

     phys=(241, 163, 49) logical=(1009, 54, 39)

Partition 2 does not end on cylinder boundary.

***@***:~$ sudo shred -vzn 0 /dev/sdc2

shred: /dev/sdc2: pass 1/1 (000000)...

***@***:~$ 

***@***:~$ 



```

i guess that was it! nice try. thank you very much for all your help coffeecat, i truly appreciate it. 
may the force be with you ;)

---

