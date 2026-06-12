---
title: "Need help - Big problem with partitions"
date: 2010-01-03
forum: General Help
---

### Post by zay2 on 2010-01-03
Hello!

I screwed up my windows installation and needed to reinstall it to fix it. I knew that this would mean system loosing grub, as i had done it before i did not think it was any big problem.

After successfully fixing my windows installation i enteded kubuntu 9.10 cd and was going to reinstall kubuntu, but kubuntu live cd did not recognize any partitions on the drive where linux and windows system disks were. 

I then ran a search for "restore ubuntu partition tables", which yielded me following results:
1) [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

2) [http://www.techrecipes.net/linux/recover-lost-partition-table-using-ubuntu-live-cd.html](http://www.techrecipes.net/linux/recover-lost-partition-table-using-ubuntu-live-cd.html)

I first tried first version 1) but if gave me an error i did not know how to fix. I then tried 2) and that screwed up things even more. Live cd recognized my partitions after that, but instead of showing linux partition as ext3 it showed it as fat32. I can mount it, but files and folders are all screwed up.

I tried fixing it with gpart again, but apparently it does not allow me to choose ext3 as partition type... gparted also fails, as it just keeps loading and loading and loading and loading...

How can i fix this, without loosing my information (i have 20+ page schoolwork on my linux drive that i need to turn in in a week :P )?

Edit1: When i try this:
```
sudo mount -t ext3 -o defaults /dev/sda2 /media/stuff/
```

```
It fails and from syslog i can read:
Jan  3 16:27:52 ubuntu kernel: [ 5445.529720] attempt to access beyond end of device
Jan  3 16:27:52 ubuntu kernel: [ 5445.529725] sda2: rw=0, want=4549803392, limit=16386237
Jan  3 16:27:52 ubuntu kernel: [ 5445.529746] attempt to access beyond end of device
Jan  3 16:27:52 ubuntu kernel: [ 5445.529751] sda2: rw=0, want=4549803392, limit=16386237
Jan  3 16:27:52 ubuntu kernel: [ 5445.529758] attempt to access beyond end of device
Jan  3 16:27:52 ubuntu kernel: [ 5445.529762] sda2: rw=0, want=4549803392, limit=16386237
Jan  3 16:27:52 ubuntu kernel: [ 5445.529774] attempt to access beyond end of device
Jan  3 16:27:52 ubuntu kernel: [ 5445.529779] sda2: rw=0, want=4549803392, limit=16386237
Jan  3 16:30:44 ubuntu kernel: [ 5617.706967] VFS: Can't find ext3 filesystem on dev sda2.
Jan  3 16:31:54 ubuntu kernel: [ 5687.704915] VFS: Can't find ext3 filesystem on dev sda2.
```



Alan

---

### Post by louieb on 2010-01-03
Please post your partition table.
```
sudo fdisk -l
``` lowercase L at the end

---

### Post by zay2 on 2010-01-03
```
ubuntu@ubuntu:/media$ sudo fdisk -l

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa063a063

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021        2040     8193118+   c  W95 FAT32 (LBA)
/dev/sda3            2041        5004    23808298+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21db21da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS
```

this /dev/sda2 should be ext3 not fat32.

Alan

---

### Post by danastasio on 2010-01-03
Well with a partition table that looks like that, i think its safe to say that whatever you did during the re-install of windows totally wiped out your linux partitions. It looks like windows took over your hard drive completley. Not sure how you can try and fix this. (if its even possible)

---

### Post by zay2 on 2010-01-03
I dont think windows wiped the drive, because after installing windows and before using gpart i COULD mount the drive (both dolphin and mount command mounted it just fine) and SEE that there was linux files on the sda2. Just that 9.04 nor 9.10 live setup could not see it... 

So i know for a fact that the info is still there. After using gpart though the filesystem was somehow changed from ext3 to fat32. Infact. If i change sda2 file system to anything less usual like linux raid autodetect it gets changed back to fat32 when i save partition table with it. 

I think that if i could change it back to ext3 (as far as i know, gpart does not have that option!), it all would be fine... 

It could be that changing it back would not work anyway, because after running gpart the fdisk -l showed bit different info, linux was /dev/sda6 then with /dev/sda5 as swap (dont rememebr, if i really had swap, but i think i didnt).

Alan.

---

### Post by marcopolo1981 on 2010-01-03
I seriously doubt that any program can convert ext3 to fat32 without it being destructive and wiping all or at least most of the data. And even if there was a way to do that, it would be virtually impossible to change it back without wiping the fat32 contents.

Just for arguments sake, if you can access the fat32 partition via windows or the live cd, do the original contents appear to be intact including the boot, root, user, etc... folders?
If so, back up everything you want then reinstall. If not, reinstall without backing up.
Using the live cd or Parted Magic live cd, you will need to delete the fat32 partition entirely, then create a new ext3/4 partition in it's place. You may need to reboot the pc in order to access the partition as ext3/4.

---

### Post by Leppie on 2010-01-03
you could try using testdisk. i believe i've read it's able to rewrite the partition table without touching the data.
```
$sudo apt-get install testdisk
$sudo testdisk
```

---

### Post by SecretCode on 2010-01-03
What version of Windows?

If you used gpart or testdisk it may not recognise partitions created by Vista or W7 and the "recovery" steps may have damaged them. Fortunately there's hope to recover.

Can you please get the "boot info script" and post the RESULTS.txt as described here: 
> **louieb said:**
> One useful tool for finding and fixing boot problems is the Boot Info Script. I often ask for the output when helping find and fix boot problems. So I put this little how to together to keep from typing the same thing over and over. (lazy). 

Special thanks to meiefra for authoring the script and making it available.  

How to get it - Download it from here. [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

How to run it:  
From a live Ubuntu CD:
Open a terminal window - Applications>Accessories>Terminal 

Type or cut n paste the following. 
```
sudo bash ~/Desktop/boot_info_script*.sh
```[COLOR=Purple]Update Karmic Live CD users [/COLOR]- the default download directory is now Downloads 
```
sudo bash ~/Downloads/boot_info_script*.sh
```

From your Ubuntu hard drive install:
Same as above unless you have changed the Firefox default download location. Then change the **~/Desktop/** part of the command to your download directory. 

You will be asked for a password - your user password. You will not see the cursor move or see any stars as you type - thats the way of the Linux terminal. Type it in and press enter.

Where to find its output: 
The script creates file RESULTS.TXT in same directory it is stored in. ~/Desktop 

Add it to your post:
Open RESULTS.TXT in your favorite text editor - cut and paste - it can be long please use code tags (the # on the tool bar) or add the file as an attachment.

Comments and suggestions are welcome.

---

### Post by zay2 on 2010-01-03
> **marcopolo1981 said:**
> I seriously doubt that any program can convert ext3 to fat32 without it being destructive and wiping all or at least most of the data. And even if there was a way to do that, it would be virtually impossible to change it back without wiping the fat32 contents.

Just for arguments sake, if you can access the fat32 partition via windows or the live cd, do the original contents appear to be intact including the boot, root, user, etc... folders?
If so, back up everything you want then reinstall. If not, reinstall without backing up.
Using the live cd or Parted Magic live cd, you will need to delete the fat32 partition entirely, then create a new ext3/4 partition in it's place. You may need to reboot the pc in order to access the partition as ext3/4.

Well. as far as i understand it did not convert the filesystem as that takes time. It probably just changed some parameter that identifies filesystem and since that parameter is wrong, the correct filesystem is not beeing recognized.. how to change that is beyond me and all that i described above is just my guess.

---

### Post by Leppie on 2010-01-03
> **SecretCode said:**
> What version of Windows?

If you used gpart or testdisk it may not recognise partitions created by Vista or W7 and the "recovery" steps may have damaged them. Fortunately there's hope to recover.

it's an ext3 partition, so the boot info script will not really be of any help since the ext3 partition is now somehow labeled as being fat and therefore cannot be mounted. the boot info script cannot access partitions that cannot be mounted.

---

### Post by zay2 on 2010-01-03
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 16386363.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 32772663.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa063a063

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,386,299    16,386,237   7 HPFS/NTFS
/dev/sda2          16,386,363    32,772,599    16,386,237   c W95 FAT32 (LBA)
/dev/sda3          32,772,663    80,389,259    47,616,597   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21db21da

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="1448B60E48B5EF1C" TYPE="ntfs" 
sda2: UUID="54AD-2D3F" TYPE="vfat" 
sda3: UUID="5828A001289FDBF6" LABEL="one_three_ntfs" TYPE="ntfs" 
sdb1: UUID="9ADC5630DC560743" LABEL="suur" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

```

The info about sda2 and sda3 is strange.. they both start at same sector?

---

### Post by marcopolo1981 on 2010-01-03
If you use the alternate install disc, when you come to formatting, you can select the partition you wish to use, then select use as... It may let you use it as ext3 again, but this is my guess, and I have nothing to back it up. It may let you, then select don't format. Then, if you get this far, you just have to reinstall grub.
But again, I'm just guessing.

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> I dont think windows wiped the drive, because after installing windows and before using gpart i COULD mount the drive (both dolphin and mount command mounted it just fine) and SEE that there was linux files on the sda2. Just that 9.04 nor 9.10 live setup could not see it... 

So i know for a fact that the info is still there. After using gpart though the filesystem was somehow changed from ext3 to fat32. Infact. If i change sda2 file system to anything less usual like linux raid autodetect it gets changed back to fat32 when i save partition table with it.

I'm not so sure that's a fact :(

Can you 
```
sudo mount -t **vfat** -o defaults /dev/sda2 /media/stuff/
```

And are there files in it?

---

### Post by zay2 on 2010-01-03
> **SecretCode said:**
> I'm not so sure that's a fact :(

Can you 
```
sudo mount -t **vfat** -o defaults /dev/sda2 /media/stuff/
```

And are there files in it?

I havent tried mounting from command line, but dolphin mounts sda2 as vfat just fine. The info is there but the filenames are huge mess.

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> I havent tried mounting from command line, but dolphin mounts sda2 as vfat just fine. The info is there but the filenames are huge mess.
so probably only the partition table was changed.

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> The info about sda2 and sda3 is strange.. they both start at same sector?

I have a theory that the 'starts at 63' refers to information in the partition sector, not the MBR, and could be relative. But that would normally only be the case in a logical partition, and these are primary partitions.

---

### Post by zay2 on 2010-01-03
> **Leppie said:**
> so probably only the partition table was changed.

[QUOTE=SecretCode]I have a theory that the 'starts at 63' refers to information in the partition sector, not the MBR, and could be relative. But that would normally only be the case in a logical partition, and these are primary partitions.[/QUOTE]

So how can i fix this?

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> So how can i fix this?

if fdisk reports errors in the partition tables, then maybe you can see what fdisk comes up with when you run it. or try to rewrite the partition table only in testdisk.

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> I havent tried mounting from command line, but dolphin mounts sda2 as vfat just fine. The info is there but the filenames are huge mess.

How much of a mess are the filenames? And how do you "know" the info is there?

---

### Post by SecretCode on 2010-01-03
Can you post the output of this command (copy & paste ... one typing error with the dd command and you could lose a lot more data):
```
sudo dd if=/dev/sda bs=1 skip=446 count=64 | hexdump -C
```

---

### Post by zay2 on 2010-01-03
> **Leppie said:**
> if fdisk reports errors in the partition tables, then maybe you can see what fdisk comes up with when you run it. or try to rewrite the partition table only in testdisk.

I could use little more information here - im quite novice user :P.
What exactly should i do/try with fdisk and what should i do with testdisk?


[QUOTE=SecretCode]How much of a mess are the filenames? And how do you "know" the info is there?[/QUOTE]

They are unreadable, meaning i cant spell them. They are just some more/less random marks. I dont "know" that. Its my guess and my hope. Otherwise i could just install it over with 9.10. But i need something from that drive. All i know that before running sudo gpart /dev/sda -W /dev/sda it was just fine. And i did not knowingly change partition type or size with it. As far as i know, i just made one partition active. So i  guess, that i could not removed/deleted/altered the data itself.

---

### Post by zay2 on 2010-01-03
> **SecretCode said:**
> Can you post the output of this command (copy & paste ... one typing error with the dd command and you could lose a lot more data):
```
sudo dd if=/dev/sda bs=1 skip=446 count=64 | hexdump -C
```
```
ubuntu@ubuntu:/media$ sudo dd if=/dev/sda bs=1 skip=446 count=64 | hexdump -C
64+0 records in
64+0 records out
64 bytes (64 B) copied, 0.0144248 s, 4.4 kB/s
00000000  00 01 01 00 07 fe ff fb  3f 00 00 00 bd 08 fa 00  |........?.......|
00000010  00 01 c1 fc 0c fe ff ff  3b 09 fa 00 bd 08 fa 00  |........;.......|
00000020  00 fe ff ff 07 fe ff ff  37 12 f4 01 55 92 d6 02  |........7...U...|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040
```

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> I could use little more information here - im quite novice user :P.
What exactly should i do/try with fdisk and what should i do with testdisk?
try this:
```
$sudo fdisk /dev/sda1
```
see if it comes up with some message about wrong filesystem/partition table information and have it repair the errors if it offers this possibility.

---

### Post by zay2 on 2010-01-03
I toyed around with fdisk exactly the way you said, and tried moving beginning of data of sda2 and sda3, but the script from before reports same stuff:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP                                  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM              

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk,   
                       sda2 starts at sector 16386363.                       
    Operating System:                                                        
    Boot files/dirs:                                                         

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk,   
                       sda3 starts at sector 32772663.                       
    Operating System:                                                        
    Boot files/dirs:                                                         


```

What should i try next? and what to do with testdisk?

While playing around with fdisk, i checked the place where you could see filesystems that are recognized and the list did not show ext3...

```
ommand action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): l

 0  Empty           24  NEC DOS         81  Minix / old Lin bf  Solaris
 1  FAT12           39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 2  XENIX root      3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 3  XENIX usr       40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 4  FAT16 <32M      41  PPC PReP Boot   85  Linux extended  c7  Syrinx
 5  Extended        42  SFS             86  NTFS volume set da  Non-FS data
 6  FAT16           4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 7  HPFS/NTFS       4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility
 8  AIX             4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt
 9  AIX bootable    50  OnTrack DM      93  Amoeba          e1  DOS access
 a  OS/2 Boot Manag 51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O
 b  W95 FAT32       52  CP/M            9f  BSD/OS          e4  SpeedStor
 c  W95 FAT32 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs
 e  W95 FAT16 (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  GPT
 f  W95 Ext'd (LBA) 55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
10  OPUS            56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
11  Hidden FAT12    5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor
12  Compaq diagnost 61  SpeedStor       a9  NetBSD          f4  SpeedStor
14  Hidden FAT16 <3 63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary
16  Hidden FAT16    64  Novell Netware  af  HFS / HFS+      fb  VMware VMFS
17  Hidden HPFS/NTF 65  Novell Netware  b7  BSDI fs         fc  VMware VMKCORE
18  AST SmartSleep  70  DiskSecure Mult b8  BSDI swap       fd  Linux raid auto
1b  Hidden W95 FAT3 75  PC/IX           bb  Boot Wizard hid fe  LANstep
1c  Hidden W95 FAT3 80  Old Minix       be  Solaris boot    ff  BBT
1e  Hidden W95 FAT1
```

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> I toyed around with fdisk exactly the way you said, and tried moving beginning of data of sda2 and sda3, but the script from before reports same stuff:
did it not give you a message saying that you might have to reboot for changes to take effect?

---

### Post by zay2 on 2010-01-03
> **Leppie said:**
> did it not give you a message saying that you might have to reboot for changes to take effect?

Nope. All it said after saving was:
```
xpert command (m for help): v
29168 unallocated 512-byte sectors

Expert command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.                             
ubuntu@ubuntu:/$ 
```

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> They are unreadable, meaning i cant spell them. They are just some more/less random marks.

So it's pretty certain it's not a valid FAT32 partition! You say you've tried changing it back to ext3, but let's try this again.

Do the following from the live cd:
*eta* Don't do this if you've made other changes! This could be destructive!


```
sudo dd if=/dev/sda of=~/ptable1 bs=1 skip=446 count=64
```
```
hexedit -s ~/ptable1 
```
Use the cursor to go to line 00000010 and position 0x14 (the position is given in the status bar at the bottom). Overtype the value 0c with 83. Press Ctrl-X to save. Then:
```
sudo dd if=~/ptable1 of=/dev/sda bs=1 seek=446 count=64
```

Then reboot the system, still to the live CD. See if *sudo fdisk -l* says the partition is 'Linux'; and try to mount it as *-t ext3*.

I'm afraid this may give the same results as in your OP, but if it sticks as 'Linux' we can try ext3 recovery tools.

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> While playing around with fdisk, i checked the place where you could see filesystems that are recognized and the list did not show ext3...
fdisk marks (almost) all linux usuable filesystems as 83 Linux.
my fdisk output looks like this:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x279d1037

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       15839   116984832    7  HPFS/NTFS
/dev/sda3           15839       25176    75000364    7  HPFS/NTFS
/dev/sda4           25177       30401    41969812+   5  Extended
/dev/sda5           25177       25298      979933+  83  Linux
/dev/sda6           25299       27122    14651248+  83  Linux
/dev/sda7           30147       30401     2048256   82  Linux swap / Solaris
/dev/sda8           27123       30146    24290248+  83  Linux

Partition table entries are not in disk order

```

however, i don't have extX partitions in my system. i'm using jfs and xfs which both are marked as 83 Linux as well.

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> While playing around with fdisk, i checked the place where you could see filesystems that are recognized and the list did not show ext3...

ext2 ext3 and ext4 are all partition type 83, 'Linux'.

---

### Post by louieb on 2010-01-03
Testdisk can change the partition type in the partition table without touching the data. I would probably try that 1st.  

if changing the file system type with testdisk does not allow you to access the data. Then  photorec which is a part of testdisk it may be your best hope  to recover any files.  

[TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by SecretCode on 2010-01-03
zay2 - have you ever installed Windows Vista or Seven on this computer? I ask because they have new partitioning rules which testdisk and other tools don't understand.

---

### Post by zay2 on 2010-01-03
> **louieb said:**
> Testdisk can change the partition type in the partition table without touching the data. I would probably try that 1st.  

if changing the file system type with testdisk does not allow you to access the data. Then  photorec which is a part of testdisk it may be your best hope  to recover any files.  

[TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")

Ok. when i try to change type, i end up at this:
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 41 GB / 38 GiB - CHS 5005 255 63

     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1  1019 254 63   16386237
 2 P Linux                 1020   1  1  2039 254 63   16386237 [NO NAME]
 3 P HPFS - NTFS           2040   1  1  5003 254 63   47616597 [one_three_ntfs]

```

Should be fine, right?
I press q to get back to previous view, and i see this:
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 41 GB / 38 GiB - CHS 5005 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  1019 254 63   16386237
 2 E extended LBA          1020   0  1  5003 254 63   64002960
 5 L Linux                 1020   1  1  2039 254 63   16386237 [NO NAME]
 6 L HPFS - NTFS           2040   1  1  5003 254 63   47616597 [one_three_ntfs]

```

Why the change? Is it all right and i should write it?

---

### Post by zay2 on 2010-01-03
> **SecretCode said:**
> zay2 - have you ever installed Windows Vista or Seven on this computer? I ask because they have new partitioning rules which testdisk and other tools don't understand.

Nope. Just XP

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> Why the change? Is it all right and i should write it?
no, don't write it yet.

---

### Post by zay2 on 2010-01-03
As i have not done any changes yet, ill try Secret's solution :)

Any objections or stuff i should be vary of?

Alan.

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> As i have not done any changes yet, ill try Secret's solution :)

Any objections or stuff i should be vary of?

Alan.
which solution? if you are going to use windows tools, then you almost certainly will to loose your data as windows does not handle foreign filesystems very well (it doesn't even handle ntfs very well...)

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> As i have not done any changes yet, ill try Secret's solution :)

Any objections or stuff i should be vary of?

Alan.

You should be wery vary of mixing up different people's advice. :) I'd rather you didn't follow my suggestions just yet if Leppie has some more things in mind.

- Especially as testdisk is proposing an extended partition, which is normal for an ubuntu install - and it includes the swap partition. Do that first.

---

### Post by zay2 on 2010-01-03
I meant this solution:
Do the following from the live cd:
*eta* Don't do this if you've made other changes! This could be destructive!


```
sudo dd if=/dev/sda of=~/ptable1 bs=1 skip=446 count=64
```
```
hexedit -s ~/ptable1 
```
Use the cursor to go to line 00000010 and position 0x14 (the position is given in the status bar at the bottom). Overtype the value 0c with 83. Press Ctrl-X to save. Then:
```
sudo dd if=~/ptable1 of=/dev/sda bs=1 seek=446 count=64
```

Then reboot the system, still to the live CD. See if *sudo fdisk -l* says the partition is 'Linux'; and try to mount it as *-t ext3*.

I'm afraid this may give the same results as in your OP, but if it sticks as 'Linux' we can try ext3 recovery tools.[/QUOTE]

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> Ok. when i try to change type, i end up at this:
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 41 GB / 38 GiB - CHS 5005 255 63

     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1  1019 254 63   16386237
 2 P Linux                 1020   1  1  2039 254 63   16386237 [NO NAME]
 3 P HPFS - NTFS           2040   1  1  5003 254 63   47616597 [one_three_ntfs]

```

Should be fine, right?
I press q to get back to previous view, and i see this:
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 41 GB / 38 GiB - CHS 5005 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  1019 254 63   16386237
 2 E extended LBA          1020   0  1  5003 254 63   64002960
 5 L Linux                 1020   1  1  2039 254 63   16386237 [NO NAME]
 6 L HPFS - NTFS           2040   1  1  5003 254 63   47616597 [one_three_ntfs]

```

Why the change? Is it all right and i should write it?

could you explain what the layout should look like again?
this disk is supposed to have 3 partitions? 2 ext3 and 1 swap?
which partition should contain what? is the first partition swap, or /?

---

### Post by zay2 on 2010-01-03
I set up the disk like that in my original install:
1) 8gb for win xp system
2) 8gb for ubuntu
3)rest of the disk i formatted ntfs.

Ubuntu then installed its of partitions on 2) i dont remember if i had swap or not, but if i remember correctly, then before using gpart 1st i had 4-5 lines in fdisk -l, and linux had 2 of them sda5 linux swap and sda6 linux. Since i dont remember if i had installed swap, i dont know if the sda5/sda6 case was wrong info it it was supposed to be like that. Lets assume it was correct.

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> before using gpart 1st i had 4-5 lines in fdisk -l, and linux had 2 of them sda5 linux swap and sda6 linux. Since i dont remember if i had installed swap, i dont know if the sda5/sda6 case was wrong info it it was supposed to be like that. Lets assume it was correct.
this would explain why testdisk wants to create the extended partition, but if you're not sure how your disk was partitioned it may be a bit more difficult to get back to the correct setup.

---

### Post by zay2 on 2010-01-03
Still its an explanation and better than nothing?

the problem with swap is, that its old pc and i cant understand why i would create swap for it, as im not using hibernate...

Anyway. If we dont have any better guesses so why not go with testdisk?

Alan

---

### Post by Leppie on 2010-01-03
yes, go ahead. i just wanted to be sure.

---

### Post by zay2 on 2010-01-03
> **Leppie said:**
> yes, go ahead. i just wanted to be sure.

```
sda1: _________________________________________________________________________                                                                                                                                   
                                                                                                                                                                                                                  
    File system:       ntfs                                                                                                                                                                                       
    Boot sector type:  Windows XP                                                                                                                                                                                 
    Boot sector info:  No errors found in the Boot Parameter Block.                                                                                                                                               
    Operating System:  Windows XP                                                                                                                                                                                 
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM                                                                                                                                                             
                                                                                                                                                                                                                  
sda2: _________________________________________________________________________                                                                                                                                   
                                                                                                                                                                                                                  
    File system:       Extended Partition                                                                                                                                                                         
    Boot sector type:  -                                                                                                                                                                                          
    Boot sector info:                                                                                                                                                                                             
                                                                                                                                                                                                                  
sda5: _________________________________________________________________________                                                                                                                                   
                                                                                                                                                                                                                  
    File system:       vfat                                                                                                                                                                                       
    Boot sector type:  Windows XP: Fat32                                                                                                                                                                          
    Boot sector info:  According to the info in the boot sector, sda5 starts                                                                                                                                      
                       at sector 63.                                                                                                                                                                              
    Operating System:                                                                                                                                                                                             
    Boot files/dirs:                                                                                                                                                                                              
                                                                                                                                                                                                                  
sda6: _________________________________________________________________________                                                                                                                                   

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.                                         
    Operating System:                                                        
    Boot files/dirs:                                                         

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:                                              
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM              

=========================== Drive/Partition Info: =============================

```

These are the results now. I have the partitions i used to have, but something is still wrong with their boot sectors.

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> These are the results now. I have the partitions i used to have, but something is still wrong with their boot sectors.

try running it again to see if it can restore correctly now.

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> These are the results now. I have the partitions i used to have, but something is still wrong with their boot sectors.

But sda5 still shows as FAT32?

---

### Post by zay2 on 2010-01-03
> **Leppie said:**
> try running it again to see if it can restore correctly now.

I ran it again. I also used the deeper search option it has, and it found all the correct partitions with correct systems. 

After saving it. fdisk -l shows:
```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            2041        5004    23808330    f  W95 Ext'd (LBA)
/dev/sda5            2041        5004    23808298+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
```

Trying to mount sda2 gives me error and syslog shows:
```
Jan  3 20:53:44 ubuntu kernel: [  310.186666] attempt to access beyond end of device
Jan  3 20:53:44 ubuntu kernel: [  310.186674] sda2: rw=0, want=4, limit=2
Jan  3 20:53:44 ubuntu kernel: [  310.186680] EXT3-fs: unable to read superblock

```

the script from page 1 shows this:
```
sda1: _________________________________________________________________________                                                                                                                                   

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP                                  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM              

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown           
    Boot sector info:                    

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.                                         
    Operating System:                                                        
    Boot files/dirs:                                                         

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:                                              
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM              

=========================== Drive/Partition Info: =============================

```

It also says unknown BootLoader on sda2

Edit:
running testdisk again gives me either results in post #44 of this thread or results like the ones in this.

Think we should somehow deal with the beginning & ending of partitions?

Edit2:
Running that deeper search with testdisk shows such results:
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 41 GB / 38 GiB - CHS 5005 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1019 254 63   16386237
D FAT32 LBA             1020   1  1  2039 254 63   16386237 [NO NAME]
D Linux Swap            1020   2  1  1143 254 63    1991934
D Linux                 1144   1  1  2039 254 63   14394177
L HPFS - NTFS           2040   1  1  5003 254 63   47616597 [one_three_ntfs]

```
Which seems to be more or less correct. When i do show files in testdisk then Linux partition has al the right stuff in it. Fat32 is beeing reported as damaged system though.

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> After saving it. fdisk -l shows:
```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            2041        5004    23808330    f  W95 Ext'd (LBA)
/dev/sda5            2041        5004    23808298+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
```

Trying to mount sda2 gives me error and syslog shows:
...
sda2 is now an extended partition - you can't mount it as a filesystem

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> Edit2:
Running that deeper search with testdisk shows such results:
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 41 GB / 38 GiB - CHS 5005 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1019 254 63   16386237
D FAT32 LBA             1020   1  1  2039 254 63   16386237 [NO NAME]
D Linux Swap            1020   2  1  1143 254 63    1991934
D Linux                 1144   1  1  2039 254 63   14394177
L HPFS - NTFS           2040   1  1  5003 254 63   47616597 [one_three_ntfs]

```
Which seems to be more or less correct. When i do show files in testdisk then Linux partition has al the right stuff in it. Fat32 is beeing reported as damaged system though.

That looks _good_. 
- The line "FAT32 LBA" should become an extended partition (no filesystem of its own). 
- The "Linux Swap" and "Linux" lines should become **L**ogical partitions not **D**eleted - change this in testdisk.
- I think this will cause testdisk to write the extended partition block one track before first logical partition, ie at 1020/1/1, correcting what it currently sees as the FAT32 partition.

---

### Post by Leppie on 2010-01-03
> **zay2 said:**
> I ran it again. I also used the deeper search option it has, and it found all the correct partitions with correct systems. 

After saving it. fdisk -l shows:
```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            2041        5004    23808330    f  W95 Ext'd (LBA)
/dev/sda5            2041        5004    23808298+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
```
it doesn't look like it found all partitions with correct filesystems.
sda6 doesn't appear anymore.

---

### Post by zay2 on 2010-01-03
I got it figured out now.

After the deeper search option in testdisk i needed to mark the linux partitions as logical (they were marked as deleted otherwise) and it saved the partition table just fine.

So i now have my files back - Big thanks to you - Leppie and to  you too Secret.

Now i just need to install grub. Can i rely on you, if that goes wrong or throws errors?

I probably should be fine if i follow this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

?

---

### Post by SecretCode on 2010-01-03
At this point I would like to make a customary recommendation for an external hard drive and clonezilla, and to make full backups of the partitions you might ever want to use again, and the MBR.

Or you could just go ahead and reinstall grub :D - it's likely to work fine!

---

### Post by zay2 on 2010-01-03
Yeah..

doing this grub-install gave me the same error again. Guess ill just install over the old linux installation - 9.10 installer can find the partitions now, so i guess this problem is solved!

And Big Thanks again to both of you!

Alan

---

### Post by SecretCode on 2010-01-03
> **zay2 said:**
> doing this grub-install gave me the same error again. 

What error is that?

---

