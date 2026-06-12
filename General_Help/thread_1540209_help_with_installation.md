---
title: "help with installation"
date: 2010-07-27
forum: General Help
---

### Post by serfa on 2010-07-27
I am trying to install Ubuntu for the first time. I had Win XP and I chose to delete it and have just Ubuntu on the hard disc. The C drive was formatted and the installation proceeded as normal but got stuck at 5% and won't go any further. It allows me to use Ubuntu as a live disc though. Help please.

---

### Post by Rubi1200 on 2010-07-27
Hi,
we need some more information in order to try and help.
 
What are your computer specifications, for example RAM, graphics card etc?
 
You say the installation stops at about 5%; are you getting error messages of any kind?
 
Also, if you can use the LiveCD and go to System > GParted and take a screenshot and post it here. You can find the screenshot program under Applications > Accessories.

---

### Post by serfa on 2010-07-28
> **Rubi1200 said:**
> Hi,
we need some more information in order to try and help.
 
What are your computer specifications, for example RAM, graphics card etc?
 
You say the installation stops at about 5%; are you getting error messages of any kind?
 
Also, if you can use the LiveCD and go to System > GParted and take a screenshot and post it here. You can find the screenshot program under Applications > Accessories.

I am not getting any error messages.
Here's the screenshot.
Memory 4 x 512MB, Nvidia Geforce 7300, Core 2 Duo Processor E6300


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   476,215,295   476,213,248  83 Linux
/dev/sda2         476,217,342   488,280,063    12,062,722   5 Extended
/dev/sda5         476,217,344   488,280,063    12,062,720  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f1e6bd08-848e-4d2c-a217-6e31117528f1   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  8d 15 42 63 99 51 7d 21  75 83 58 b7 a2 d1 46 df  |..Bc.Q}!u.X...F.|
00000010  19 ba 5b a2 3e 88 92 a4  27 d0 6d 3b 4b d4 1a e1  |..[.>...'.m;K...|
00000020  f4 dc 83 5c 68 b1 d9 c7  1b 1c c6 15 50 2d d2 6a  |...\h.......P-.j|
00000030  ca b8 26 27 af 4e d0 83  9d b4 7e 10 9b 66 82 85  |..&'.N....~..f..|
00000040  cc 73 69 24 9c 5a d8 0e  19 21 64 a0 2b cb de 79  |.si$.Z...!d.+..y|
00000050  b3 83 2b 85 69 c9 49 0c  e0 f2 27 5b a8 03 b8 ff  |..+.i.I...'[....|
00000060  94 c9 14 dd af d9 e5 9b  04 ec 09 5e e5 b8 35 b4  |...........^..5.|
00000070  fa 97 2c 6b 1b 3f 08 71  e1 20 63 61 5b 42 3b e1  |..,k.?.q. ca[B;.|
00000080  80 69 e3 7f 05 a7 91 ae  88 f3 9d 03 2e 71 ba a5  |.i...........q..|
00000090  c8 0e c2 c7 5f 9f 67 a7  35 79 b2 a9 c4 29 6a 24  |...._.g.5y...)j$|
000000a0  5e ef bb ff 6a f6 c0 0c  98 cc ae cd da 4b 1c 7f  |^...j........K..|
000000b0  b3 37 db 57 6a e7 93 52  94 71 4c 4b 50 1c 02 fb  |.7.Wj..R.qLKP...|
000000c0  23 7d 7c 1d 0d 66 57 f3  69 e4 c5 80 07 10 15 2d  |#}|..fW.i......-|
000000d0  6d 77 8a 24 fd 5e b7 78  77 79 37 d4 55 73 7d 5f  |mw.$.^.xwy7.Us}_|
000000e0  8a 57 10 d4 d1 ba 77 20  6c b5 ef 19 04 bd b5 eb  |.W....w l.......|
000000f0  75 6a 5c ae 8f 90 65 15  9f 33 f9 44 13 6c 48 91  |uj\...e..3.D.lH.|
00000100  5d eb 5b 2b cc 28 6c de  4d 60 13 7b 7f b4 b6 b8  |].[+.(l.M`.{....|
00000110  b9 f1 f8 8f 55 3a 6f 5b  34 8b 3d 54 b4 ec e4 e3  |....U:o[4.=T....|
00000120  ff f8 9c d8 4c 1b df 63  a7 ec 34 f4 18 39 47 f0  |....L..c..4..9G.|
00000130  4e 47 1e de e4 63 97 2d  a2 0e 1d 74 90 8f b0 59  |NG...c.-...t...Y|
00000140  e6 bd ae ae 82 9b 27 36  e1 20 86 18 5b 64 17 5b  |......'6. ..[d.[|
00000150  3d 77 62 14 3e 42 fd ef  5f f6 ca a4 90 fb 3c 1d  |=wb.>B.._.....<.|
00000160  db a2 bd 12 fa 66 18 90  6f f5 d7 75 da 8f 3a 16  |.....f..o..u..:.|
00000170  05 af db 37 52 dc 9c fe  29 b7 fd d7 ac da 18 c8  |...7R...).......|
00000180  a1 23 f6 a4 31 58 a9 5a  cf c6 3b 6e a3 99 c5 f6  |.#..1X.Z..;n....|
00000190  f7 69 93 b8 80 a1 13 e2  bb 76 4d 91 30 d2 9f 9a  |.i.......vM.0...|
000001a0  58 a9 39 ce 1c 4f 45 37  e1 38 9d d2 b1 b6 ba 80  |X.9..OE7.8......|
000001b0  8b 39 47 61 62 2d 7a 76  38 e9 0a ad 17 72 00 fe  |.9Gab-zv8....r..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 10 b8 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by george051685 on 2010-07-28
**Re: nVidia latest Drivers - How to install** 			
 			 			 		   		 		 		ok i need some  help im new to the linux os i am still trying to learn it and im trying  to install a 9800gt nvidia graphics card on my ubuuntu i have been  reading forums for the last 5 days and still no luck i managed to do a  install and it is giving me the following errors

distribution pre install script failed

install failed /var/log/nvidia-installer.log

unable to load kernal module 'nvidia,ko,

any help to get this issue fixed would be much appreciated i am trying to run compiz

---

### Post by Rubi1200 on 2010-07-29
Hi serfa,
thanks for the information. Personally, I do not see any obvious problems (not that I am an expert though).
 
I have a couple of suggestions:
 
Boot the computer with the LiveCD and choose the option to check the disk for defects and see if any error messages come up.
 
If everything comes back normal, use GParted and format the main partition, sda1 from the screenshot, to ext4. You will have to unmount the swap partition to do so; right-click and choose Swapoff.
 
Reboot and try installing again.
 
Let us know what happens.
 
Good luck!

---

### Post by dino99 on 2010-07-29
prepare your hdd before installation:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by serfa on 2010-07-29
> **dino99 said:**
> prepare your hdd before installation:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

I can boot with the normal CD but not with the alternate version.
Where do I go from here?

---

### Post by Rubi1200 on 2010-07-29
> **serfa said:**
> I can boot with the normal CD but not with the alternate version.
Where do I go from here?
 
I suggest you boot with the normal LiveCD and use GParted to format the drive. First, right-click on the swap partition and choose Swapoff. Then delete all the partitions there including the 1MB at the beginning of the drive.
 
I think the best option for formatting the drive would probably be ext4 since that is what Ubuntu will use by default.
 
Then, reboot using the CD and choose to check the disk for defects. If everything is okay go ahead and install Ubuntu and let it choose the default options including for the swap partition.
 
If you run into problems or if anything is unclear, feel free to ask.

---

### Post by serfa on 2010-08-03
> **Rubi1200 said:**
> I suggest you boot with the normal LiveCD and use GParted to format the drive. First, right-click on the swap partition and choose Swapoff. Then delete all the partitions there including the 1MB at the beginning of the drive.
 
I think the best option for formatting the drive would probably be ext4 since that is what Ubuntu will use by default.
 
Then, reboot using the CD and choose to check the disk for defects. If everything is okay go ahead and install Ubuntu and let it choose the default options including for the swap partition.
 
If you run into problems or if anything is unclear, feel free to ask.

No luck yet with the installation. The Disk Utility tells me there are 7 bad sectors. If these are at the beginning of the disk it would explain why XP - the previous OS - wouldn't boot. I am now trying moving the partition to the right and trying again.

---

### Post by serfa on 2010-08-06
> **serfa said:**
> No luck yet with the installation. The Disk Utility tells me there are 7 bad sectors. If these are at the beginning of the disk it would explain why XP - the previous OS - wouldn't boot. I am now trying moving the partition to the right and trying again.

It won't let me move the partition. I have decided there is some thing physically wrong with the disk so I am giving up. Thanks Rubi for your help.

---

