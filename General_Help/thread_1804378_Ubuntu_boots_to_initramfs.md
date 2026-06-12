---
title: "Ubuntu boots to initramfs"
date: 2011-07-14
forum: General Help
---

### Post by Bugs318 on 2011-07-14
This morning I ran an upgrade which upgraded the kernel from 2.6.35-28 to 2.6.35-30 on my Maverick system.  I then departed for a meeting and came back to discover that my system had rebooted itself and only booted into an initramfs prompt.

Rebooting again shows a very brief flashing message of "error: unknown filesystem" alongside a few other errors I cannot read in the 1/4 second the error lasts on screen before the grub prompt.

Neither kernel boot nor recovery mode options take me anywhere except to the initramfs prompt.

I have searched and found a few threads on similar issues, but they all involve different fixes and suggest causes (such as dual booting on an ntfs drive, which I do not do) such that I am unsure where to go from here.

Any prompt help would be greatly appreciated!

---

### Post by drs305 on 2011-07-14
Can you boot another kernel?

If you don't have another kernel on the menu but one is in your /boot folder, you can manually edit the Grub menu entry (press 'e' on the entry) to point to the correct (older) kernel. To see what's available, if it's not on the menu:
Press 'c' to get to the prompt, then for your Ubuntu partition (example hd0,5)
```
ls (hdX,Y)/boot
``` 

If you download/extract/run the boot info script and post the contents of the RESULTS.txt from the following site we can take a look at your boot status:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It's also possible the initrd image needs to be updated, but that will be a bit more complicated, so try the above options and we'll see if we can repair it by those means.

---

### Post by Bugs318 on 2011-07-14
Thanks so much for your prompt reply and assistance!!!

I cannot boot either kernel, nor either recovery mode (that is, all kernels boot to initramfs).

Before I post the Results.txt info, I just thought I'd mention that upon using a livecd, I cannot mount any of my partitions and I receive the following error:

"Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda9,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Here is the text of the RESULTS.txt file:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sda9,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 32.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,101   968,960,474   949,425,374   5 Extended
/dev/sda5          19,535,103    58,605,119    39,070,017  83 Linux
/dev/sda6          58,605,183    97,675,199    39,070,017  83 Linux
/dev/sda7          97,675,263   136,745,279    39,070,017  83 Linux
/dev/sda8         136,745,343   175,815,359    39,070,017  83 Linux
/dev/sda9         175,815,423   965,072,744   789,257,322  83 Linux
/dev/sda10        965,072,808   968,960,474     3,887,667  82 Linux swap / Solaris
/dev/sda3         972,864,270   976,768,064     3,903,795  82 Linux swap / Solaris
/dev/sda4         968,960,475   972,864,269     3,903,795  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.1 GB, 16053698560 bytes
5 heads, 32 sectors/track, 195968 cylinders, total 31354880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  32    31,354,879    31,354,848  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        997d9b48-ea27-4049-8bd1-6d06b27fc88b   ext4       
/dev/sda10                                              swap       
/dev/sda3                                               swap       
/dev/sda4                                               swap       
/dev/sda6        a1d7efa1-c63e-4970-af0b-10bcb6bfc2f7   ext4       
/dev/sda7        26fe82d5-06d3-484e-bff3-46b290fd3869   ext4       
/dev/sda8        13cb214c-848c-46f2-b51e-cdb3f79853d6   ext4       
/dev/sda9        f1f5db60-aebc-42cb-908b-d5fc83b9c72c   ext3       
/dev/sdb1        A78B-0602                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/A78B-0602         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5

00000000  01 00 00 00 00 00 00 00  00 00 86 60 00 00 00 00  |...........`....|
00000010  01 00 00 00 00 00 00 00  00 00 e2 60 00 00 00 00  |...........`....|
00000020  01 00 00 00 00 00 00 00  00 00 86 60 00 00 00 00  |...........`....|
00000030  01 00 00 00 00 00 00 00  00 00 e2 60 00 00 00 00  |...........`....|
00000040  01 00 00 00 00 00 00 00  00 00 86 60 00 00 00 00  |...........`....|
00000050  01 00 00 00 00 00 00 00  00 00 e2 60 00 00 00 00  |...........`....|
00000060  01 00 00 00 00 00 00 00  00 00 86 60 00 00 00 00  |...........`....|
00000070  01 00 00 00 00 00 00 00  00 00 e2 60 00 00 00 00  |...........`....|
00000080  01 00 00 00 00 00 00 00  00 00 86 60 00 00 00 00  |...........`....|
00000090  01 00 00 00 00 00 00 00  00 00 e2 60 00 00 00 00  |...........`....|
000000a0  57 15 86 60 00 00 00 00  01 00 00 00 00 00 00 00  |W..`............|
000000b0  00 00 86 60 00 00 00 00  01 00 00 00 00 00 00 00  |...`............|
000000c0  00 00 e2 60 00 00 00 00  01 00 00 00 00 00 00 00  |...`............|
000000d0  00 00 86 60 00 00 00 00  01 00 00 00 00 00 00 00  |...`............|
000000e0  00 00 e2 60 00 00 00 00  00 e0 6f 02 00 10 00 80  |...`......o.....|
000000f0  00 f0 eb 39 00 10 00 00  00 00 00 c3 8d b6 00 00  |...9............|
00000100  55 89 e5 8b 45 08 5d 8b  40 0c 8b 40 0c 8b 80 bc  |U...E.].@..@....|
00000110  00 00 00 c3 8d b6 00 00  00 00 8d bf 00 00 00 00  |................|
00000120  55 89 e5 8b 45 08 5d 8b  40 0c 8b 40 0c 8b 80 c0  |U...E.].@..@....|
00000130  00 00 00 c3 8d b6 00 00  00 00 8d bf 00 00 00 00  |................|
00000140  55 89 e5 8b 45 08 5d 8b  40 0c 8b 40 0c dd 80 c4  |U...E.].@..@....|
00000150  00 00 00 c3 8d b6 00 00  00 00 8d bf 00 00 00 00  |................|
00000160  55 89 e5 53 83 ec 14 8b  45 08 e8 18 5f ff ff 81  |U..S....E..._...|
00000170  c3 75 df 01 00 8b 40 0c  8b 40 04 89 04 24 e8 75  |.u....@..@...$.u|
00000180  56 ff ff 83 c4 14 5b 5d  c3 8d b4 26 00 00 00 00  |V.....[]...&....|
00000190  55 89 e5 81 ec 88 00 00  00 89 5d f4 e8 e6 5e ff  |U.........]...^.|
000001a0  ff 81 c3 43 df 01 00 89  75 f8 89 7d fc 8b 7d 08  |...C....u..}..}.|
000001b0  c7 04 24 0c 00 00 00 e8  2c 5b ff ff 89 3c 24 89  |..$.....,[...<$.|
000001c0  c6 e8 32 56 ff ff c7 45  a8 00 00 00 00 89 06 8b  |..2V...E........|
000001d0  45 0c 89 46 04 8b 45 10  89 46 08 8b 47 0c 8b 10  |E..F..E..F..G...|
000001e0  c7 04 24 08 00 00 00 89  55 a4 e8 a9 58 ff ff 89  |..$.....U...X...|
000001f0  00 10 61 4d 00 10 00 80  c7 8d 83 fc 38 fe ff 89  |..aM........8...|
00000200

```

---

### Post by Bugs318 on 2011-07-14
I ran fsck in the livecd due to the noted mount errors.  It fixed some inode errors, and the partitions could then mount within the livecd, so I tried rebooting.  It was apparently booting fine until an error appeared saying that /home couldn't boot since it was listed as ext3.  Since it is actually formatted as ext4 (as are all of my partitions) I altered /etc/fstab to read ext4 and rebooted again.  The system started booting as normal but then halted mid-boot with the following as some of the error lines:

mountall: Event failed
init: ureadahead-other main process (1292) terminated with status 4
init: statd-mounting main process (1294) killed by TERM signal

The /home partition messages read as follows (and are similar to the message on the other drives, but I received similar message ever since installing):

/dev/sda9: clean, 123168/24666112 files, 47544229/98657165 blocks
init: statd main process(1148) terminated with status 1
init: statd main process ended, respawning
init: statd main process(1155) terminated with status 1
init: statd main process ended, respawning
init: statd main process(1162) terminated with status 1
init: statd main process ended, respawning
init: statd main process(1169) terminated with status 1
init: statd respawning too fast, stopped

---

### Post by Bugs318 on 2011-07-14
Hmmm, then after fscking again in the livecd and rebooting, I selected the old kernel, which boots fine, but the newer kernel won't boot all the way, crashing and giving me disk errors.  If I then fsck them again I can boot but only into the old kernel.

Is this a bug?

---

### Post by drs305 on 2011-07-14
> **Bugs318 said:**
> Hmmm, then after fscking again in the livecd and rebooting, I selected the old kernel, which boots fine, but the newer kernel won't boot all the way, crashing and giving me disk errors.  If I then fsck them again I can boot but only into the old kernel.

Is this a bug?

The full contents of RESULTS.txt doesn't appear to have been copied but it looks like the system is progressing past the Grub handing regardless.

I'm not familiar with the error messages. Try booting the old kernel, then running the following command to rebuild the latest initrd image:
```

sudo update-initramfs -k <version>
```
Example:
sudo update-initramfs -u -k 2.6.38-8-generic

Use whatever kernel is the top entry in your menu list (i.e. the one that is causing the problem). You can see the menu entries with:
```
grep "menuentry" /boot/grub/grub.cfg
```

---

### Post by New2computer on 2011-07-14
Hey guys, I am having same problem on ubuntu 10.4. this is second time it happed to me. First time I was marking around with command line and than after reboot i could no longer boot into ubuntu. I thought i have done something in command line but second time after complete re installation i did nothing and very shortly (couple of month) same thing again, computer boots into initramfs. I have read some previous discussions on that matter but all inconclusive. I need to recover some documents from it. Second system is windows xp. Any suggestions and more importantly can I really rely on ubuntu, because this is second time in row, maybe i am doing something wrong? 

Cheers

---

### Post by drs305 on 2011-07-15
> **New2computer said:**
> Hey guys, I am having same problem on ubuntu 10.4. this is second time it happed to me. First time I was marking around with command line and than after reboot i could no longer boot into ubuntu. I thought i have done something in command line but second time after complete re installation i did nothing and very shortly (couple of month) same thing again, computer boots into initramfs. I have read some previous discussions on that matter but all inconclusive. I need to recover some documents from it. Second system is windows xp. Any suggestions and more importantly can I really rely on ubuntu, because this is second time in row, maybe i am doing something wrong? 

Cheers

New2computer,

Welcome to the Ubuntu forums. Although your symptoms may be the same, it would be best to start your own thread. Include a description of your problem and also the contents of RESULTS.txt.

You generate the RESULTS.txt by booting a LiveCD, going to the following link, and downloading/running the boot info script.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Bugs318 on 2011-07-15
Going away for vacation and don't have time to run this fix attempt, but I will try it when I return and post back in a week and a half, and I do appreciate the assistance immensely!

---

### Post by jukzh on 2011-11-07
Hi there!

Want to say many thanks to all the people who worked on boot-repair, it's a real magical, app!
I'm just a poor student, otherwise i'd donate :P i kid you not.

I had 40G hard with XP on it and 20G of it I used to install Ubuntu, from liveCD, but after install grub menu won't show up, directly booting into XP, then i did grub install, which gave me a 'grub>' at boot time, and specifying kernel and initrd, would led to '(initramfs)' busybox, due to not finding /sbin/init :confused:
Well, thats behind now!

Thanks again community, for proving that computing is for everyone!

---

