---
title: "recover lost root partition /dev/sda7 after rsync"
date: 2012-08-27
forum: General Help
---

### Post by dragonfly41 on 2012-08-27
I have a Dell laptop in dual boot mode .. I'm still using Ubuntu 10.10.

my windows boot partitions were here .. ([COLOR=Blue]/dev/sda1 to /dev/sda6[/COLOR] )
Windows Vista /dev/sda3/ type=ntfs
internal_data /dev/sda6/ type=ntfs

my ubuntu boot partitions were here .. ([COLOR=Blue]/dev/sda7 and /dev/sda8[/COLOR])
Ubuntu 10.10 (/) /dev/sda7/ type=ext4
Ubuntu 10.10 (/home) /dev/sda8/ type=ext4

I have ubuntu 10.10 installed on external USB drive /dev/sdb1/  (root+home in one partition) and  I decided to offload files from my dual boot ubuntu into ubuntu on my USB drive.  

I booted into my external ubuntu (F12 to boot into USB) and then used rsync to start moving some files from the internal ubuntu mounted partitions to my USB ubuntu.  
The idea was to get them into sync without doing a full clone using clonezilla.

In rsync commands I used the mounted labels .. (these were noted before this crash).
[COLOR=Blue]
/dev/sda7: UUID="8eeb2f0d-92c7-463e-8961-3a1241fc148a" TYPE="ext4"        ubuntu_root
/dev/sda8: UUID="13f48ffa-cafb-48cd-aa6a-6d3acf4e69ee" TYPE="ext4"           ubuntu_home[/COLOR]

Rsync started working o.k.

I copied several directories from /dev/sda8 (my home partition) into my USB ubuntu. 

Here is an example of one of the rsync commands ..

[COLOR=Blue]sudo rsync -avz  /media/13f48ffa-cafb-48cd-aa6a-6d3acf4e69ee/myusername/public_html/   ~/public_html/[/COLOR]

I used Gnome Commander to check that the file transfers were o.k.

Then I tried copying from /dev/sda7/ into my USB drive

[COLOR=Blue]sudo rsync -avz /media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/usr/share/apache2/ ~/usr/share/apache2/[/COLOR]

Now this didn't work and I shut down at that point to try again later.

Today I booted up as usual but .. disaster .. no grub menu seen .. only

[COLOR=Blue]error: unknown filesystem
grub rescue >[/COLOR]

Could that last rsync command - which failed to complete before I shut down - have screwed up the root partition?

I can boot into the Windows partition and using the ext2 file explorer in windows confirms that the ubuntu root partition /dev/sda7/ cannot be seen. 

What advice to recover my lost ubuntu root partition /dev/sda7/?

---

### Post by dragonfly41 on 2012-08-27
I've done some more research

In fact I booted into Vista and used some linux recovery tools (only installed in trial mode so I could not complete the recovery) to see if the tools could find the lost ext4 partition.

Two different tools found it ..

Raise Data Recovery for ext2/3/4
[www.usfexplorer.com](www.usfexplorer.com)

Drive:0   Fixed ATA TOSHIBA MK2546GSX

In /dev/sda

unknown partition (sector 380755968, 29.29 GB)

partition start 380755968 (0x16B1E000)
partition end 442189824 (0x1A5B3800)
partition size 61433856 (0x03A96800)

29.29 GB

this is the lost /dev/sda7 root partition

................

Then I tried Stellar Phoenix Linux Data Recovery
[www.stellarinfo.com](www.stellarinfo.com)

This tool also identified the lost partition directory structure (see image partition_recovery.jpg attached below).

................

I don't want to have to purchase a licence for these tools if it's not necessary.

Using the partition start and partition end data above can testdisk recover the above found partition?

Or perhaps ddrescue?

Thanks.

---

### Post by oldfred on 2012-08-27
May be best to use Boot-Repair first and run the BootInfo report just to document system.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Testdisk can often find old or missing partitions.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

But if you moved NTFS partitions around you will have issues. NTFS partitions have the start and size in the PBR or partition boot sector that must match the partition table. Also Windows only boots from a primary partition with the boot flag, but grub does not use boot flag nor need it to chain load to Windows.

---

### Post by dragonfly41 on 2012-08-28
Well I tried testdisk but I seem to be sinking deeper into the mire.

After trying testdisk to recover /dev/sda7

I cannot now boot into either windows vista partition or ubuntu partition in my /dev/sda

I can only boot (via F12) into external USB ubuntu (as I'm running now) in /dev/sdb as my only means of recovery.

From my working ubuntu I can see in Toolbar > "Places"

[LIST]
[*][COLOR=Blue]34 GB File System[/COLOR]  .. (which in Nautilus shows 0 items, free space 11.5 GB)
[/LIST]

[LIST]
[*][COLOR=Blue]internal_data[/COLOR]  (ntfs partition in /dev/sda) .. which in Nautilus shows 20 items, free space 59.4 GB)
[/LIST]

[LIST]
[*][COLOR=Blue]31 GB File System[/COLOR] (which on trying to mount reads .. Unable to mount 31 GB File System - error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or helper program, or other error
[/LIST]

[LIST]
[*][COLOR=Blue]MEDIADIRECT[/COLOR] (unused .. from Dell) .. opens in Nautilus
[/LIST]

[LIST]
[*][COLOR=Blue]21 GB File System[/COLOR] (old backups of /root and /home partitions)
[/LIST]

[LIST]
[*][COLOR=Blue]external_data[/COLOR] (ntfs partition in /dev/sdb) .. opens o.k. in Nautilus
[/LIST]


[COLOR=DarkRed]Note: "internal" refers to /dev/sda in my laptop, "external" refers to /dev/sdb in my USB drive.   So external_ntfs is a partition in my USB drive.
[/COLOR] 

=================================

When I ran gparted it displayed /dev/sda as "unallocated, cannot host a partition outside the disk"

=================================

Then running  [COLOR=Blue]sudo testdisk[/COLOR] ...

[COLOR=Blue]Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT16 >32M               0   1  1    24 254 63     401562 [DellUtility]
 2 P FAT32 LBA               25   0  1  4202 254 63   67119570 [NO NAME]
 3 P HPFS - NTFS          14078 221 32 23700 213  1  154576896 [internal_data]
 4 E extended LBA         23701   0  1 30401 254 63  107651565
 5 L Linux                24247 252  6 28072  17 41   61433856
   X extended             30074 238  1 30401  42 41    5240948
 6 L FAT32 LBA            30074 239 54 30401  42 41    5240832 [MEDIADIRECT][/COLOR]

============================================

I carried on deeper search in testdisk and saw this .. (I don't know why sectors are in duplicate although there is reference to sector backups?)

[COLOR=Blue]Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

Read error at 1418/21/37 (lba=22781529)

at 95% of testdisk "deep search" ...

  FAT16 >32M               0   1  1    24 254 63     401562 [DellUtility]
  FAT32 LBA               25   0  1  4202 254 63   67119570 [NO NAME]
  FAT32 LBA               25   0  1  4202 254 63   67119570 [NO NAME]
  HPFS - NTFS             25  29  5  1330 135 21   20971520 [RECOVERY]
  HPFS - NTFS             25  29  5  1330 135 21   20971520 [RECOVERY]
  HPFS - NTFS           1330 135 22 14078 188 55  204799993 [Vista]
  HPFS - NTFS           1330 135 29 14078 188 62  204799993
  HPFS - NTFS          14078 221 32 23700 213  1  154576896 [internal_data]
  HPFS - NTFS          14078 221 32 23700 213  1  154576896 [internal_data]
  Linux                24247 252  6 28072  17 41   61433856
  Linux                24248  62  7 28072  82 42   61433856
  Linux                27525  43 39 30074 207 21   40960000
[/COLOR]

then as 100% is reached testdisk jumps to this much shorter display
[COLOR=Blue]
The harddisk (250 GB / 232 GiB) seems too small! (< 266 GB / 248 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                29901 111 35 32451  20 17   40960000
  Linux                29901 176 36 32451  85 18   40960000
  Linux                29903  89 11 32452 252 56   40960000
  Linux                29903 219 13 32453 127 58   40960000[/COLOR]


When I continue I get a new screen .. (see testdisk.jpg attached)

[COLOR=Blue]Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    24 254 63     401562 [DellUtility]
D FAT32 LBA               25   0  1  4202 254 63   67119570 [NO NAME]
D HPFS - NTFS             25  29  5  1330 135 21   20971520 [RECOVERY]
D HPFS - NTFS           1330 135 21  2635 241 37   20971520
D HPFS - NTFS           1330 135 22 14078 188 55  204799993 [Vista]
[COLOR=Red]D HPFS - NTFS           1330 135 29 14078 188 62  204799993[/COLOR]
P HPFS - NTFS          14078 221 32 23700 213  1  154576896 [internal_data]
D Linux                24247 252  6 28072  17 41   61433856
D Linux                24248  62  7 28072  82 42   61433856
D Linux                27525  43 39 30074 207 21   40960000
P FAT32 LBA            30074 239 54 30401  42 41    5240832 [MEDIADIRECT]
[/COLOR]
When I scroll down to the unnamed Vista partition it says ..
[COLOR=Blue]
NTFS found using backup sector! 104 GB / 7 GB[/COLOR]

Where do I go from here to recover Vista partition?

Recovery of Vista is now more important than recovering the /root Linux partition since I have an old backup of /root.

---

### Post by oldfred on 2012-08-28
Every time you change partitions some is saved as testdisk seems to find all the old versions, even if minor changes. You then can restore an older partition or missing partition, but cannot overlap other partitions. 

All NTFS partitions have to have a Windows partition boot sector  (PBR) with the same start & size info as the partition. Testdisk can find the backup to a PBR, but it has to be the version that matchs. If not then you have to use a Windows repairCD or USB to fix the boot sector and run chkdsk.

---

