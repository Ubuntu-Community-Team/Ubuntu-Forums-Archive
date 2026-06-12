---
title: "partitioning advice."
date: 2010-10-01
forum: General Help
---

### Post by jquis8411 on 2010-10-01
Hello Ubuntu community:
I have desktop running 10.04  with a 160 GB HDD (150 ext4, 6.5gd swap) that is slowly becoming a file/print server. I decided to add a 500 gb hard drive and thought I should seek some advice before formatting and partitioning it. The network its on is shared with windows and Ubuntu machines. I do plan on adding more HDD's down the road as they fill up fast. I just didn't want to paint myself into a corner by not planning this out. TY

---

### Post by srs5694 on 2010-10-01
If you expect to be making rapid changes, I recommend using an LVM configuration for the best possible flexibility. Unfortunately, Ubuntu makes LVM setup harder than it could be, but it can certainly be done. Try Googling "Ubuntu LVM" for some information.

The best approach is probably to set up a couple of smallish partitions for /boot partitions on the new 500GB drive (I say a couple so that you'll be able to do future OS installations more easily), set up the rest as an LVM, and transfer your current system into the LVM. When you're satisfied it's booting, you can then remove the partitions from the old 160GB drive, create a new LVM partition on it, and add it to the LVM. You'll then be able to add new disks as they become necessary, and remove smaller ones if you need to do so to make room for the new ones.

---

### Post by holiday on 2010-10-01
I was just looking into this for myself and found this great thing

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by jquis8411 on 2010-10-02
Thanks for the Link Holiday, I saw that and thought "I'm good to go". But I started looking into LVM now and it seems like a good idea, now this could be inexperience talking but with LVM could I just give each user their own shared volume to play with and set properties for it?  And would LVM in anyway cause problems with Samba or SSH?

---

### Post by srs5694 on 2010-10-02
Personally, I wouldn't give each user a separate logical volume in an LVM configuration; I'd just set up a single logical volume for /home and create accounts normally. If you need to limit how much disk space individual users are consuming, you can look into Linux's quota features. (Try Googling "Linux disk quotas" for information on this topic.) Quotas are much more flexible than using separate logical volumes for each user; there'll be less hassle to set up new accounts, and you can easily adjust quotas up or down as the need arises. (If you were to use separate logical volumes, you'd need to resize them to achieve such changes, and that would be both risky and more effort.)

LVM won't cause problems with Samba, SSH, or other servers; these servers all operate on a high enough level that they don't "see" such low-level details as the use of regular partitions vs. LVM, or even what filesystem is being used. (The servers will benefit or suffer from performance effects, of course, the same as any other program.)

---

### Post by dino99 on 2010-10-02
mountmanager can help you set rights as you need

---

### Post by holiday on 2010-10-02
I had one LVM and did not enjoy the experience, but perhaps I didn't give it enough of a try. I'll read up on it, but perhaps someone could give a rationalization for using them, or give us some reasons to not.

---

### Post by jquis8411 on 2010-10-02
I did see some things that recommended against using LVM with the desktop edition of Ubuntu, I was not sure if it was just some bad luck or something though because I cant imagine what the difference between the server edition and desktop would be, except a GUI of course.

---

### Post by srs5694 on 2010-10-02
> **holiday said:**
> I had one LVM and did not enjoy the experience, but perhaps I didn't give it enough of a try. I'll read up on it, but perhaps someone could give a rationalization for using them, or give us some reasons to not.

Reasons to use LVM:


[list]
[*]Easily combine space from smaller disks or disk fragments into a big filesystem. For instance, if you've got three 80 GB hard disks, you can create a single filesystem that's up to 240 GB in size.
[*]Increase speed in multi-disk setups by using LVM's striping feature, which interleaves one filesystem across two or more disks, thus spreading the load and increasing performance.
[*]Easily add, delete, and resize logical volumes without having to adjust other filesystems. For instance, in a conventional partitioning scheme, if you've got /dev/sda1, /dev/sda2, and /dev/sda3, in that order on the disk, and if you want to delete /dev/sda1 and add the space to /dev/sda3, you've got to move /dev/sda2 -- a potentially time-consuming and risky task. If all three filesystems were in LVM, you could do the equivalent without touching the LVM equivalent of /dev/sda2. This is because LVM works a lot like a filesystem, and logical volumes are like files -- they can be discontiguous, unlike partitions, which must remain contiguous.
[*]Add future disks to a current LVM setup, enabling expansion of existing partitions into the new disk space without creating new mount points, moving files, etc.
[*]Delete old disks from a current LVM setup without having to explicitly juggle files. (This assumes there's sufficient free space in the LVM to absorb the storage space being lost by deleting the old disks.)
[/list]


Reasons to avoid LVM:


[list]
[*]Increases complexity of setup; normally, you'll use LVM atop normal partitions, which adds to the set of tools you need to use. Even if you use LVM without a partition table, LVM tools are more numerous and complex than partitioning tools like fdisk or GParted. (OTOH, LVM GUI utilities can simplify its configuration, so this isn't really all that huge a drawback.)
[*]Increase the risk of data loss -- if one disk fails, recovering data from the other disk(s) can be difficult. Using LVM atop a suitable RAID setup can minimize this risk, but at the cost of added complexity. AFAIK, TestDisk can't recover the individual logical volumes within an LVM. (I don't know offhand if TestDisk can identify and recover a lost LVM partition.)
[*]GParted can't resize logical volumes; however, other GUIs, such as kvpm and system-config-lvm, can do the job instead. (This is therefore a minor drawback, but I mention it because GParted is well understood by the Ubuntu community as a whole, whereas the LVM GUI tools are not as well understood.)
[*]Booting from LVM may require a separate /boot partition. (True of GRUB Legacy; not true of GRUB 2.) This is a very minor issue, since you can easily create a suitable partition when you install or convert to LVM.
[*]The Ubuntu installer provides poor LVM support, making initial LVM setup by newbies very difficult. (Note that this isn't true of all distributions. Fedora, for instance, provides LVM support in its installer that makes it pretty easy to set up LVM.)
[*]Non-Linux support for Linux's LVM is poor, so if you want to create a shared-data partition, it will have to reside outside of the LVM, thus reducing the flexibility of the system overall. That is, if you want to change the size of the shared-data partition, you'll have all the usual partition-management headaches, and transferring space between a shared-data partition and a logical volume can be still more complex.
[/list]


There are probably other issues for both the "pro" and the "con" lists; these are just the issues that sprang immediately to mind.

Personally, I like LVM. Four of my six Linux installations use LVM. I am, however, an advanced Linux user. If Ubuntu provided Fedora's level of LVM support, I'd say that even newbies should consider using it; but as it is, new Ubuntu users are usually best served sticking the conventional partitions. I recommended it to jquis8411 because s/he plans to add disk space in the future, perhaps multiple times in the future. That's the sort of dynamic system for which LVM provides significant benefits.

---

### Post by jquis8411 on 2010-10-02
Well I grabbed LVM2 from synaptic and it doesn't look all that intimidating.(but I have only known how to cut and paste for less than a year so I'm prob a poor judge) But here is my plan so far, 1) on the new HDD (500GB) create a boot partition, but Im not sure how big. 2) Make all the remaining space one big LVM partition which I can then break down into smaller logical volumes as I see fit. 3)figure out how to get my stuff (OS included) off the old HDD and onto the new one, then create another LVM partition on the old HDD and tie it all together..Hows this sound,  Am I on the right track?

---

### Post by holiday on 2010-10-02
> **srs5694 said:**
> Reasons to use LVM:


[list]
[*]Easily combine space from smaller disks or disk fragments into a big filesystem. For instance, if you've got three 80 GB hard disks, you can create a single filesystem that's up to 240 GB in size.
[*]Increase speed in multi-disk setups by using LVM's striping feature, which interleaves one filesystem across two or more disks, thus spreading the load and increasing performance.
[*]Easily add, delete, and resize logical volumes without having to adjust other filesystems. For instance, in a conventional partitioning scheme, if you've got /dev/sda1, /dev/sda2, and /dev/sda3, in that order on the disk, and if you want to delete /dev/sda1 and add the space to /dev/sda3, you've got to move /dev/sda2 -- a potentially time-consuming and risky task. If all three filesystems were in LVM, you could do the equivalent without touching the LVM equivalent of /dev/sda2. This is because LVM works a lot like a filesystem, and logical volumes are like files -- they can be discontiguous, unlike partitions, which must remain contiguous.
[*]Add future disks to a current LVM setup, enabling expansion of existing partitions into the new disk space without creating new mount points, moving files, etc.
[*]Delete old disks from a current LVM setup without having to explicitly juggle files. (This assumes there's sufficient free space in the LVM to absorb the storage space being lost by deleting the old disks.)
[/list]


Reasons to avoid LVM:


[list]
[*]Increases complexity of setup; normally, you'll use LVM atop normal partitions, which adds to the set of tools you need to use. Even if you use LVM without a partition table, LVM tools are more numerous and complex than partitioning tools like fdisk or GParted. (OTOH, LVM GUI utilities can simplify its configuration, so this isn't really all that huge a drawback.)
[*]Increase the risk of data loss -- if one disk fails, recovering data from the other disk(s) can be difficult. Using LVM atop a suitable RAID setup can minimize this risk, but at the cost of added complexity. AFAIK, TestDisk can't recover the individual logical volumes within an LVM. (I don't know offhand if TestDisk can identify and recover a lost LVM partition.)
[*]GParted can't resize logical volumes; however, other GUIs, such as kvpm and system-config-lvm, can do the job instead. (This is therefore a minor drawback, but I mention it because GParted is well understood by the Ubuntu community as a whole, whereas the LVM GUI tools are not as well understood.)
[*]Booting from LVM may require a separate /boot partition. (True of GRUB Legacy; not true of GRUB 2.) This is a very minor issue, since you can easily create a suitable partition when you install or convert to LVM.
[*]The Ubuntu installer provides poor LVM support, making initial LVM setup by newbies very difficult. (Note that this isn't true of all distributions. Fedora, for instance, provides LVM support in its installer that makes it pretty easy to set up LVM.)
[*]Non-Linux support for Linux's LVM is poor, so if you want to create a shared-data partition, it will have to reside outside of the LVM, thus reducing the flexibility of the system overall. That is, if you want to change the size of the shared-data partition, you'll have all the usual partition-management headaches, and transferring space between a shared-data partition and a logical volume can be still more complex.
[/list]


There are probably other issues for both the "pro" and the "con" lists; these are just the issues that sprang immediately to mind.

Personally, I like LVM. Four of my six Linux installations use LVM. I am, however, an advanced Linux user. If Ubuntu provided Fedora's level of LVM support, I'd say that even newbies should consider using it; but as it is, new Ubuntu users are usually best served sticking the conventional partitions. I recommended it to jquis8411 because s/he plans to add disk space in the future, perhaps multiple times in the future. That's the sort of dynamic system for which LVM provides significant benefits.

Great post. Thanks.

---

### Post by srs5694 on 2010-10-02
> **jquis8411 said:**
> Well I grabbed LVM2 from synaptic and it doesn't look all that intimidating.(but I have only known how to cut and paste for less than a year so I'm prob a poor judge) But here is my plan so far, 1) on the new HDD (500GB) create a boot partition, but Im not sure how big. 2) Make all the remaining space one big LVM partition which I can then break down into smaller logical volumes as I see fit. 3)figure out how to get my stuff (OS included) off the old HDD and onto the new one, then create another LVM partition on the old HDD and tie it all together..Hows this sound,  Am I on the right track?

In broad outline, yes, that should work. To help fill in a couple of details:


[list]
[*]I find that 200MB is plenty for a /boot partition. It's got to hold whatever's in your current /boot directory, which is likely to be well under half that amount. Making it 200MB gives you plenty of space if you need to have multiple kernels installed for some reason.
[*]For copying your existing system over, you could use any number of backup/copy programs. Personally, I use tar. To do it this way, first create a filesystem on the new logical volume and mount it somewhere convenient (say, /mnt). Then type "cd /; sudo tar --create --one-file-system --file . | (cd /mnt; sudo tar xvf -)". This will copy the contents of the root (/) partition to /mnt. If you have more than one partition in your current installation, you'll have to repeat that command for each one, changing the cd commands appropriately. Use ls or a file browser to verify that the copy looks sane, and "df -h" to check that the total amount of space consumed on the new system looks sane. (The total amount may differ slightly from the original, but not hugely so.)
[*]Once everything's copied, update your current system's GRUB configuration to include the new system. Reboot to test it. If you can successfully boot, you can make equivalent changes to the new system's GRUB configuration and re-install GRUB from there. Boot loader problems can render the system unbootable until you resolve them. I recommend being prepared by having on hand a copy of the [Super GRUB Disk.](http://www.supergrubdisk.org/) Try booting using it before you do anything else so you know how it works.
[/list]

---

### Post by jquis8411 on 2010-10-03
OK so I think things were going well with setting up LVM but I go to format my boot sector to ext3 and I get a message saying, "mke2fs : inode size (128) * inodes_ count (0) too big for a file system with no blocks, specify higher inode_ratio (-i) or lower inode count (-n)."  I'm not exactly sure how to proceed from here. I went with all the default values while setting up in fdisk.  I'll attach what I did so you can see if it looks like I goofed.

---

### Post by jquis8411 on 2010-10-03
Just in case no one wants to open that attachment...
joe@joe-desktop:~$ sudo apt-get install lvm2
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
joe@joe-desktop:~$ sudo modprobe dm-mod
joe@joe-desktop:~$ sudo partprobe
joe@joe-desktop:~$ sudo fdisk /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): c
DOS Compatibility flag is not set

Command (m for help): u
Changing display/entry units to sectors

Command (m for help): m      
Command action
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

Command (m for help): p

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005684e

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
e
Partition number (1-4): 2
First sector (2048-976773167, default 2048): 2048
Last sector, +sectors or +size{K,M,G} (2048-976773167, default 976773167): +200M

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
e
Invalid partition number for type `e'
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Partition number (1-4): 3
First sector (411648-976773167, default 411648): 
Using default value 411648
Last sector, +sectors or +size{K,M,G} (411648-976773167, default 976773167): 
Using default value 976773167

Command (m for help): t
Partition number (1-5): 3
Hex code (type L to list codes): l

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
Hex code (type L to list codes): 8e
Changed system type of partition 3 to 8e (Linux LVM)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
joe@joe-desktop:~$ sudo partprobe
[sudo] password for joe: 
joe@joe-desktop:~$ cat /etc/fdisk
cat: /etc/fdisk: No such file or directory
joe@joe-desktop:~$ sudo mke2fs -j /dev/sdb2
mke2fs 1.41.11 (14-Mar-2010)
mke2fs: inode_size (128) * inodes_count (0) too big for a
    filesystem with 0 blocks, specify higher inode_ratio (-i)
    or lower inode count (-N).

joe@joe-desktop:~$ -n
-n: command not found
joe@joe-desktop:~$ sudo mke2fs -j -n /dev/sdb2
mke2fs 1.41.11 (14-Mar-2010)
mke2fs: inode_size (128) * inodes_count (0) too big for a
    filesystem with 0 blocks, specify higher inode_ratio (-i)
    or lower inode count (-N).

joe@joe-desktop:~$ sudo mke2fs -j -i /dev/sdb2
mke2fs: invalid inode ratio /dev/sdb2 (min 1024/max 65536)
joe@joe-desktop:~$

---

### Post by srs5694 on 2010-10-04
It looks like you created /dev/sdb2 as an *extended* partition, which is a special kind of primary partition that does nothing but hold logical partitions. You can't create a filesystem on an extended partition. You should go back into fdisk, delete /dev/sdb2, and re-create it as a *primary* partition. Alternatively, you can leave /dev/sdb2 as an extended partition and create a new logical partition (/dev/sdb5) within it and use that as your /boot partition; however, having /boot as a primary partition gives you more options for how to configure GRUB, and since you've only got two partitions on the disk, having them both be primaries shouldn't be a problem.

---

### Post by jquis8411 on 2010-10-04
Alright I got that all straightened out TY. Now should I make logical partitions for swap and stuff then just copy everything into its respective spots?

---

### Post by srs5694 on 2010-10-04
You can use the LVM for swap space, or you can create partitions for that, as you see fit. (A partition might work better if you intend to use suspend-to-disk functionality, but I'm not positive of that.) Consult one of the many Web pages on LVM configuration for details of creating and using it.

---

