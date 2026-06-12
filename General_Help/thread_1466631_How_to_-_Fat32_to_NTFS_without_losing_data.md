---
title: "How to? - Fat32 to NTFS without losing data"
date: 2010-04-30
forum: General Help
---

### Post by Cigla on 2010-04-30
Hi everybody! 
During Ubuntu(10.04-64bit) installation I have accidently marked NTFS partitions to be used as FAT32, without marking them for formatting. Few seconds after I pressed the Install button, installation reported an error, something like "Can't mount the partition..", reffering to one  of mentioned partitions. I went few steps back, and than I realized what I've done. Now I can't mount any of those partitions, GParted can't reckognize file system (unknown), also I can't boot to Windows which was on one of partitions, seems to be a lot of damage done in a short time, but I can't believe it is unfixable? (There was no formatting?)
I tried to repeat the installation (but now with 9.10 32bit, thought it might be a problem with 10.04) , with proper marking for those partitions, but partitioner doesn't offer NTFS system anymore.  Windows partition (55GiB) is marked as FAT32, other partitions(220GiB and 290GiB) are marked as *unknown*(see the attachment). Those partitions are full of valuable data, and I can't afford losing them.
Anyone can help on this?

---

### Post by koanhead on 2010-04-30
I googled round a bit and found this thread:

[http://ubuntuforums.org/showthread.php?t=503195](http://ubuntuforums.org/showthread.php?t=503195)

basically, it sounds like you need ntfs-3g and ntfsprogs (the latter may be optional but it will be nice to have if you are keeping the ntfs partition around)
hth

---

### Post by dino99 on 2010-04-30
some good tools:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)
[http://partedmagic.com/](http://partedmagic.com/)

if you can boot on a live-cd, then you can try to chroot your lucid partition, following this post (give your real path):

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

if that work, then you can run: sudo grub-mkconfig && update-grub
( be sure there is no more grub-legacy packages installed remove/purge); only grub-pc & grub-common have to be installed)

That should let you boot now. Hope partedmagic or cgsecurity can repair the windows mbr.

---

### Post by itachisxeyes on 2010-04-30
so, we have a data recovery issue. 
you might want to try "data carving tools" since all the files where probably already marked for deletion but (hopefully) where not deleted 
they also suggest that you do a full image of the drive first...so if you mess up you didn't just bomb your only copy of the data XD

---

### Post by Cigla on 2010-04-30
I didn't have this problem before, during the installation of Ubuntu 9.10; I could choose NTFS from drop down menu. Does that mean that I have ntfs-3g already (GParted from live CD), and that problem is in something else? I understand that GParted has all features enabled when it is ran from live CD.  
Since I can't install anything while running live session, do you mean I should install Ubuntu first, then ntfs-3g, and then try to mount the partitions? I didn't need anything before to do so; now Ubuntu just don't reckognize the file system

---

### Post by itachisxeyes on 2010-04-30
> **Cigla said:**
> I didn't have this problem before, during the installation of Ubuntu 9.10; I could choose NTFS from drop down menu. Does that mean that I have ntfs-3g already (GParted from live CD), and that problem is in something else? I understand that GParted has all features enabled when it is ran from live CD.  
Since I can't install anything while running live session, do you mean I should install Ubuntu first, then ntfs-3g, and then try to mount the partitions? I didn't need anything before to do so; now Ubuntu just don't reckognize the file system

well unless i have miss read your original post, you had valuable data on that partition that isn't being recognized now, right? so you don't want to go formating it until your sure you can't get any data off of it.
so yeah you could try doing that. just make sure not to install on un recognized partition

---

### Post by lavinog on 2010-04-30
What version of windows was it?
vista and 7 have a repair program on the install disks.

---

### Post by dino99 on 2010-04-30
the question is : is Lucid well installed or not ? That's why i gave you a better tool " partedmagic": you boot with it then its able to format, repair and more .

---

### Post by Cigla on 2010-04-30
Previous post was reply to **koanhead**, thanks for helping anyway, but I already tried something similar**,** andproblem remains[B].

@dino99:[/B] I don't understand very well what actually happened here, you think that MBR is also damaged? Is it possible that it is just boot partition damaged, I thought MBR is independent from any partition? Can I just install Ubuntu without mounting those damaged partitions, and then install those tools you proposed?
Thanks

**@itachisxeyes:** Unfortunally, I don't have where to back up that amount of data (500GiB), so I have to try something else.Thanks anyway.

---

### Post by Cigla on 2010-04-30
> **lavinog said:**
> What version of windows was it?
vista and 7 have a repair program on the install disks.

It was fresh installed Win XP SP3, I downgraded from Win7.
So you suggest I try Win7 installation disk? 
Do you mean I have to install Win7 first?

---

### Post by Cigla on 2010-04-30
> **dino99 said:**
> the question is : is Lucid well installed or not ? That's why i gave you a better tool " partedmagic": you boot with it then its able to format, repair and more .

Sorry, I can _boot_ with it ? OK, then I'll try that and come back here with results.

---

### Post by zuerston on 2010-04-30
> **Cigla said:**
> Hi everybody! 
During Ubuntu(10.04-64bit) installation I have accidently marked NTFS partitions to be used as FAT32, without marking them for formatting. Few seconds after I pressed the Install button, installation reported an error, something like "Can't mount the partition..", reffering to one  of mentioned partitions. I went few steps back, and than I realized what I've done. Now I can't mount any of those partitions, GParted can't reckognize file system (unknown), also I can't boot to Windows which was on one of partitions, seems to be a lot of damage done in a short time, but I can't believe it is unfixable? (There was no formatting?)
I tried to repeat the installation (but now with 9.10 32bit, thought it might be a problem with 10.04) , with proper marking for those partitions, but partitioner doesn't offer NTFS system anymore.  Windows partition (55GiB) is marked as FAT32, other partitions(220GiB and 290GiB) are marked as *unknown*(see the attachment). Those partitions are full of valuable data, and I can't afford losing them.
Anyone can help on this?
I used to make a set of 4 floppy disks (in boot directory of Windows CD) and boot from first floppy disk ,run console term when choice comes up and type "fixboot" and then type "fixmbr" to get it back when messed up.

---

### Post by psusi on 2010-04-30
NO NO NO DO NOT RUN THE WINDOWS FIXING GARBAGE!

If you changed the partition type from ntfs to fat32, then the Windows fixer will replace the ntfs boot sector with a fat32 one, totally hosing your system.

Check the output of blkid from the livecd and see if it recognizes the fs as ntfs.  Also you can use fdisk to change the partition type back to fat32.  Do this:

sudo fdisk /dev/sda

You will get a prompt.  Enter p to print the partition table.  Enter t to tag the partition type.  It will ask you which partition you want to change, then ask you for the partition type code.  It will tell you to enter L for a list of codes.  Enter the one for NTFS.  After that print the table again to make sure it looks good ( only thing different should be the type code ) and enter w to write it and quit.

---

### Post by zuerston on 2010-04-30
> **psusi said:**
> NO NO NO DO NOT RUN THE WINDOWS FIXING GARBAGE!

If you changed the partition type from ntfs to fat32, then the Windows fixer will replace the ntfs boot sector with a fat32 one, totally hosing your system.

Check the output of blkid from the livecd and see if it recognizes the fs as ntfs.  Also you can use fdisk to change the partition type back to fat32.  Do this:

sudo fdisk /dev/sda

You will get a prompt.  Enter p to print the partition table.  Enter t to tag the partition type.  It will ask you which partition you want to change, then ask you for the partition type code.  It will tell you to enter L for a list of codes.  Enter the one for NTFS.  After that print the table again to make sure it looks good ( only thing different should be the type code ) and enter w to write it and quit.

Sounds like you been there too! yup Windows is GARBAGE! 
I used to say ohhh well,  "its just magnetic crap on a disk!" it never existed in the first place :P

---

### Post by Cigla on 2010-04-30
> **psusi said:**
> NO NO NO DO NOT RUN THE WINDOWS FIXING GARBAGE!

If you changed the partition type from ntfs to fat32, then the Windows fixer will replace the ntfs boot sector with a fat32 one, totally hosing your system.

Check the output of blkid from the livecd and see if it recognizes the fs as ntfs.  Also you can use fdisk to change the partition type back to fat32.  Do this:

sudo fdisk /dev/sda

You will get a prompt.  Enter p to print the partition table.  Enter t to tag the partition type.  It will ask you which partition you want to change, then ask you for the partition type code.  It will tell you to enter L for a list of codes.  Enter the one for NTFS.  After that print the table again to make sure it looks good ( only thing different should be the type code ) and enter w to write it and quit.

[SIZE=2]This is the output of blkid:[/SIZE]
[INDENT][SIZE=1]ubuntu@ubuntu:~$ blkid
/dev/sda1: UUID="9EEC-76A8" TYPE="vfat" 
/dev/sda10: UUID="3c7fe0af-5dfd-4ce6-8618-e08b7b9387be" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="5af294bb-27bd-429a-9cac-5e4ecd230075" TYPE="swap" 
/dev/sda8: UUID="079c62e3-b6e3-4ac4-a87c-f2c6fc22c97d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="376b8150-3a6c-47e4-a345-f0824eb4ccc7" SEC_TYPE="ext2" TYPE="ext3" [/SIZE]
[/INDENT]
[SIZE=2]I don't see here those damaged partitions, except windows partition (reckognized as fat32, probably?) 

The output of fdisk:[/SIZE]
[INDENT][LEFT][SIZE=1]sudo fdisk /dev/sda

The number of cylinders for this disk is set to 77825.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8a5d8a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7180    57673318+   b  W95 FAT32
/dev/sda2            7181       77825   567455932    5  Extended
/dev/sda5            7181       35899   230685336    b  W95 FAT32
/dev/sda6           35900       73909   305315293+   b  W95 FAT32
/dev/sda7           73910       74170     2096451   82  Linux swap / Solaris
/dev/sda8           74171       74555     3092481   83  Linux
/dev/sda9           74556       75273     5767303+  83  Linux
/dev/sda10          75274       77825    20498908+  83  Linux
[/SIZE][/LEFT]
[/INDENT][INDENT][SIZE=1]Command (m for help): t
Partition number (1-10): 1
Hex code (type L to list codes): L

 0  Empty           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 1  FAT12           39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 2  XENIX root      3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 3  XENIX usr       40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 4  FAT16 <32M      41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 5  Extended        42  SFS             **86  NTFS volume set da**  Non-FS data    
 6  FAT16           4d  QNX4.x          **87  NTFS volume set db**  CP/M / CTOS / .
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
Hex code (type L to list codes): [/SIZE]
[/INDENT][SIZE=2]Should I now enter the code 86 or 87?[/SIZE]

---

### Post by pcura on 2010-04-30
Just a question though, how many partitions do you have on ubuntu though? from what I've read in some thread/s is that 4 partitions is the maximum. 

still a newbie with ubuntu though but the way i see it you have more than 4 partitions. Probably that is whats causing the problem.

---

### Post by psusi on 2010-04-30
You want 7.  86 and 87 are windows soft raid.  It looks like you already have had the boot sector replaced with a fat one though.  Are you sure you did not format it in gparted, or run the windows fixboot stuff?

> **pcura said:**
> Just a question though, how many partitions do you have on ubuntu though? from what I've read in some thread/s is that 4 partitions is the maximum. 

still a newbie with ubuntu though but the way i see it you have more than 4 partitions. Probably that is whats causing the problem.

The MSDOS partition table can have only 4 primary partitions.  You can make one of those an extended partition though and put as many logical partitions in there as you want.

---

### Post by Cigla on 2010-04-30
@**[B]psusi**:
What you are trying to tell me here is that only partition tags are changed, so that's why they are not reckognized? Sounds very logical to me, 'cause everything happened very quickly, and I can't believe that something big could change in that time.
 Just, this windows partition is acting odd in comparison with other two. This could be because of their different sizes? (50GiB Vs 200GiB) Those are just my guessings, since I know that FAT32 is ment to be used for small partitions. I will use that partition as experimental, since nothing important[/B]**(Win)**[B] is there.

@pcura:No, that is not the problem, I'm sure.You can have as many partitions as you want, as far as I know.I use them for /, /usr and /home. 

@psusi: I have Ubuntu 9.10 32bit installed, was dual boot with Windows 7; until yesterday, when I installed Windows XP - which probably overwrited MBR. I was aware of that installing windows will erase grub loader, but I did it anyway since I have planned to switch to Ubuntu 10.04 64bit today.
[/B]

---

### Post by Cigla on 2010-04-30
I will try now tagging the windows partition using Hex code 7 as you recommended

---

### Post by psusi on 2010-04-30
> **Cigla said:**
> @**[B]psusi**:
What you are trying to tell me here is that only partition tags are changed, so that's why they are not reckognized? Sounds very logical to me, 'cause everything happened very quickly, and I can't believe that something big could change in that time.
 Just, this windows partition is acting odd in comparison with other two. This could be because of their different sizes? (50GiB Vs 200GiB) Those are just my guessings, since I know that FAT32 is ment to be used for small partitions. I will use that partition as experimental, since nothing important[/B]**(Win)**[B] is there.

Not quite.  At FIRST it sounds like you only changed the partition type tag, which Linux completely ignores anyhow.  Windows however, will get very confused and I have seen it try to "fix" this by writing a new fat boot sector instead, trashing the fs.  Since blkid says it is vfat, that actually checks the boot sector to see what it is, so it seems somehow you have trashed at least that part.  You might try using testdisk to recover.

---

### Post by Cigla on 2010-05-02
> **psusi said:**
> Not quite. At FIRST it sounds like you only changed the partition type tag, which Linux completely ignores anyhow. Windows however, will get very confused and I have seen it try to "fix" this by writing a new fat boot sector instead, trashing the fs. Since blkid says it is vfat, that actually checks the boot sector to see what it is, so it seems somehow you have trashed at least that part. You might try using testdisk to recover.
> **dino99 said:**
> the question is : is Lucid well installed or not ? That's why i gave you a better tool " partedmagic": you boot with it then its able to format, repair and more .
 
I have ran testdisk using partedmagic 4.10 and informations found [***here***]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") (thanks dino99) I followed the described procedure, and after Deeper Search got some promising results; damaged partitions are found and reckognized as NTFS. I can even expore file system on boot/windows partition, which isn't the case for other two partitions. 
First thing that I find unusuall, different than in documentation example, is that those two partition's starts are not at the right place. [***Here***]("http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical") I found that *logical partition's start is _usually_ a non-null cylinder, head 1, sector 1*. That is not my case. How serious damage is this? Or, is that damage at all?
Now, I ve decided to try with Advanced procedure described at the bottom of [***this***]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples#of_reformatted_partition") page, but there is still one question for which I can't find the answer in this documentation: **How can I be sure of what is my partition table type?** I choose Intel/PC, which is highlited by default, but later I get error:"*The harddisk (640 GB / 596 GiB) seems too small! (<1017 GB / 947 GiB) Check the harddisk size: HD jumpers settings, BIOS detection..*.". The capacity of my HD is 640GB, and it is well reckognized, so why is testdisk complaining? At the very beggining, at step 1, when I have to select media, disk capacity is correctly detected, but later, testdisk expects something bigger(?)Should I ignore that message and continue with recovery procedure?
I have the feeling that whole this thing is going to work, but it is impossible without your assistance, so I'm waiting for your respond..

---

### Post by Cigla on 2010-05-16
I managed to recover all data using Testdisk, using example given at the bottom of [*this*]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples") page.
Seems that just boot sectors of partitions were changed. Data was there, but unreadable because of this. Fortunately, every partition has backup boot sector.
I want to thank everybody for helping me.

---

