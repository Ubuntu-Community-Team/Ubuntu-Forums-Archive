---
title: "Ipod not working now, but it was yesterday."
date: 2009-07-26
forum: General Help
---

### Post by CaptainMark on 2009-07-26
Ive been using my ipod quite happily with banshee until recently i plug it in and it doesnt mount, i tried plugging it in to my girlfriends laptop with windows and i get nothing, not detected. I put in a terminal sudo fdisk -l and detected the ipod ```
mark@mark-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4d78be6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59578   478560253+  83  Linux
/dev/sda2           59579       60801     9823747+   5  Extended
/dev/sda5           59579       60801     9823716   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdg: 119.8 GB, 119832539136 bytes
26 heads, 50 sectors/track, 22504 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       22505   117023708    b  W95 FAT32
mark@mark-desktop:~$ 


```so i tried manually mounting ```
mark@mark-desktop:~$ sudo mount -t vfat /dev/sdg1 /media/IPOD/ 
mount: /dev/sdg1: can't read superblock
mark@mark-desktop:~$ 


``` and no luck, i dont know what this error means, i tried googling but couldnt understand the results as im still a noob. 
Has my ipod become an expensive paperweight, whats caused this, i dont know. 
Any help, its only a few months old.

---

### Post by Bigtime_Scrub on 2009-07-26
I don't think you are going to like answer man...

Have you tried resetting the iPod? if you hold the top button on the scroll wheel and the center buttom at the same time for awhile it usually resets it. You should see an Apple logo pop up. 

Or you can try the force command.


```
sudo mount -t vfat /dev/sdg1 /media/IPOD/ -o force
```

If you do the force command please post the output here.

---

### Post by CaptainMark on 2009-07-26
[LEFT]Tried resetting a millon and one times already. Heres output of forced mount ```
mark@mark-desktop:~$ sudo mount -t vfat /dev/sdg1 /media/IPOD/ -o force
[sudo] password for mark: 
mount: wrong fs type, bad option, bad superblock on /dev/sdg1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```
[/LEFT]

---

### Post by Bigtime_Scrub on 2009-07-26
Now I am no expert at this but I think the drive sdg1 is corrupted or it is just not being read properly. Let's be certain:

Please post the output of

```
dmesg | tail
```

Lets see if that gives us more info.

Also please post the output of

```
cat /etc/fstab
```

---

### Post by CaptainMark on 2009-07-26
Heres both, i tried adding the mount line to fstab already and running sudo mount -a, nothing again ```
mark@mark-desktop:~$ dmesg | tail
[  490.678232] Buffer I/O error on device sdg1, logical block 0
[  490.678241] Buffer I/O error on device sdg1, logical block 1
[  490.678245] Buffer I/O error on device sdg1, logical block 2
[  490.678249] Buffer I/O error on device sdg1, logical block 3
[  503.934335] sd 7:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  503.934343] sd 7:0:0:0: [sdg] Sense Key : Medium Error [current] 
[  503.934349] Info fld=0x0
[  503.934352] sd 7:0:0:0: [sdg] Add. Sense: Unrecovered read error
[  503.934357] end_request: I/O error, dev sdg, sector 512
[  503.934364] Buffer I/O error on device sdg, logical block 64
mark@mark-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d59f291a-b2fe-4335-b6ca-3a4a181d01db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

### Post by Bigtime_Scrub on 2009-07-26
Does the iPod turn on? Like I said I am no expert and if someone else knows for sure please post. I think it is bricked. I would try to sync it to iTunes under Windows and pray somehow that Apple firmware can somehow fix it. 

You can also try for iPod specific help on a Mac forum. They may know a little more about their own products. Sometimes they have obscure tips or Apple can sometimes be pursuaded to replace their hardware for free.

---

### Post by CaptainMark on 2009-07-28
Yeah i think its flunked. I do hate apple and everything they stand for but when i logged an online technical problem at apple.com some UPS bloke turned up at work the next day to take my ipod to the ipod hospital. They said its poorly.

---

