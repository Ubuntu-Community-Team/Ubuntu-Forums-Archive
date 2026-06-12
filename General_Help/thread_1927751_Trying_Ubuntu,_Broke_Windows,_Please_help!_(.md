---
title: "Trying Ubuntu, Broke Windows, Please help! :("
date: 2012-02-18
forum: General Help
---

### Post by S2005 on 2012-02-18
So, I'll start at the beginning. I have a Micro-SD card that got corrupted and I wanted the files off of it. I read that there was no way to do it, and I'd have to format it. :( I found this unacceptable. I read deeper. Somewhere I read that it could be done in Linux. I have an old BackTrack3 disk, and I tinkered around in there with it. I read that I'd need something more. I got Ubuntu 11.1 (I think that's the version).

I tinkered around in Ubuntu trying commands that I found on forums to repair the "superblock." I'd like to mention here, that I am NOT good at Linux. I have only ever used it to recover deleted files on a hard drive, and to crack a WEP key a long time ago. I am worse than a noobie, as I soon proved to myself.

I had to go to work, so I gave up on the Micro-SD card temporarily. I shut down. Upon coming home, I wanted to play some Star Wars:TOR, so I booted up, and now my Windows won't boot. It goes all the way to the graphic (the swirly windows symbol), starts the graphic, and then blue screens for a fraction of a second, and reboots. I tried booting in recover mode, I tried the Windows disk, nothing will repair it. 

I loaded Ubuntu back up (from CD) and have been trying a few commands, but I have no idea what I am doing. I am probably causing more damage than good.   

$fdisk -l
> Disk /dev/sdc: 90.0 GB, 90028302336 bytes
255 heads, 63 sectors/track, 10945 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition tableThis is the drive. It's a 90GB OCZ-Agility3 SSD. I'm using Win7x64.

Also, to note, it does not show up at all in my Home Folder. I have 2 other drives that do show up.

> *-disk:1
       description: ATA Disk
       product: OCZ-AGILITY3
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdc
       version: 2.15
       serial: OCZ-44MSYHT4Z73OZ5IA
       size: 83GiB (90GB)
       configuration: ansiversion=5
In summary, I have no idea what to try. I don't know what I broke. I can remember most of the commands I attempted, and I think I was using the wrong /dev.

---

### Post by pedja_portugalac on 2012-02-18
The best program for recovering partitions, sectors etc is called TestDisk [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

TestDisk can

    Fix partition table, recover deleted partition
    Recover FAT32 boot sector from its backup
    Rebuild FAT12/FAT16/FAT32 boot sector
    Fix FAT tables
    Rebuild NTFS boot sector
    Recover NTFS boot sector from its backup
    Fix MFT using MFT mirror
    Locate ext2/ext3/ext4 Backup SuperBlock
    Undelete files from FAT, exFAT, NTFS and ext2 filesystem
    Copy files from deleted FAT, exFAT, NTFS and ext2/ext3/ext4 partitions. 

TestDisk has features for both novices and experts. For those who know little or nothing about data recovery techniques, TestDisk can be used to collect detailed information about a non-booting drive which can then be sent to a tech for further analysis. Those more familiar with such procedures should find TestDisk a handy tool in performing onsite recovery.

---

### Post by S2005 on 2012-02-18
Thank you very much for the reply Pedja!

Do I make a bootable disk with TestDisk? or does it run from ubuntu?

/Ninja Edit

I downloaded it, and I'm going to try to figure it out now.  Thank you Pedja!

/Another Edit

Ok, I downloaded it... but I have no clue what to do now... I am used to windows... there is no .exe file... how do I use Testdisk?

---

### Post by pedja_portugalac on 2012-02-18
You can run it in many ways. Last time I was using [http://www.sysresccd.org/SystemRescueCd_Homepage]("http://www.sysresccd.org/SystemRescueCd_Homepage") 
It's easy, read this [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by S2005 on 2012-02-18
The directions say: 
> Under Unix/Linux/BSD, you need to be root to run TestDisk (ie. sudo testdisk-6.9/linux/testdisk_static)

Do I type that into terminal? I tried, and it says command not found...

I typed:
> sudo testdisk-6.13/linux/testdisk_static
and
> sudo testdisk-6.9/linux/testdisk_static

---

### Post by S2005 on 2012-02-18
Still nothing :(  I can't anything.   It says No partition found.  and   No partition is bootable.  I feel I am just going to lose everything on that drive... and have to reinstall Win... :(

---

