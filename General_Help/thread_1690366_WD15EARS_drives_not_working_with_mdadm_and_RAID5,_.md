---
title: "WD15EARS drives not working with mdadm and RAID5, especially after reboot"
date: 2011-02-18
forum: General Help
---

### Post by coinmagic45 on 2011-02-18
Hi and thanks for taking a look at my thread!

I am getting really frustrated with trying to get my RAID5 working again.  I had a RAID5 array built with 4 of the Western Digital 1.5tb "Advanced Format" drives, WD15EARS.  However, when copying 1.5gb dvd encoded files to the drive, I was getting speeds of ~2mb/s.  When researching how to make this faster, I came across all the posts about the Advanced Format drives and how that was causing a lot of issues for a lot of people.  It looked like the solution was simple enough: partition starting at sector 64 or 2048 or whatever and then recreate the RAID.  However, this is not working for me.  I have been posting back and forth with a few people on [this]("http://forums.sagetv.com/forums/showthread.php?t=53523&page=3") thread on the sage tv forum.  But it's been a week and I'm getting more and more frustrated, so I'm hoping someone on the Ubuntu forums can help :-)

Here are my computer specs:
**Motherboard:** Gigabyte GA-EP43-DS3L LGA 775 Intel P43 ATX
**CPU:** Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W
**RAM:** 4gb DDR2 1066 (PC2 8500)
**Video card:** ASUS GeForce 9600GT 512MB 256-bit
**Linux:** 10.04

I have gone through quite a few iterations of trying to make this all work.  You can see our paper trail in the other thread.  Most recently, here is what I did:

**********************************

0. Used mdadm --zero-superblock for everything to do with drives sdb, sdc, sdd, sde.

1. Wrote zeroes to the ENTIRE drive for drives sdb, sdc, sdd, sde using:
dd if=/dev/zero of=/dev/sdb bs=1M #did the same for sdc, sdd, sde
#This was a suggestion from the Sage tv forum to clear everything from the drive and hopefully start from scratch.

2. Deleted the old /etc/mdadm/mdadm.conf

3. Updated the initramfs stuff using:
update-initramfs -u
#Prior to doing this, the mdadm.conf file stored in there was referencing my very 1st RAID array rather than all my failed attempts after that, even though I created a new /etc/mdadm/mdadm.conf file each time.


  From here, I had (in theory) 4 completely "fresh" drives and my computer new  nothing of my old RAID array.  So, I went through the steps of creating a  new one:

**Step 1**. Use parted to create the partitions:
```
parted -a optimal /dev/sdb
mklabel gpt
u s
mkpart

ext3
2048
2930277128
q
```I did this for drives sdb, sdc, sdd, sde.

**Step 2**. Use gparted to create an ext3 file system on each of these drives.  I  then set the raid flag using gparted.  I know this is probably  unnecessary, but I figured it doesn't hurt (and I had a bit of spare  time).

** Step 3**. Reboot.  After reboot, gdisk still showed the partitions there and starting at the correct sector (2048).

**Step 4**. Create RAID:
```
sudo mdadm --create --verbose /dev/md0 --level=5 --chunk=256 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

mdadm: layout defaults to left-symmetric
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=1465137540K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=1465137540K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=1465137540K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sde1 appears to contain an ext2fs file system
    size=1465137540K  mtime=Wed Dec 31 19:00:00 1969
mdadm: size set to 1465137408K
Continue creating array? y
mdadm: array /dev/md0 started.
```**Step 5**. Update /etc/mdadm/mdadm.conf by creating a new mdadm.conf file in  /etc/mdadm, putting "DEVICE partitions" on the 1st line, and then  copy-pasting the output of:
```
sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=75da0b4c:5f50fdbe:b401dda8:b6a22f08
```** Step 6**. Use "update-initramfs -u" to update that.

**Step 7**. Create ext3 file system:
```
sudo mkfs.ext3 /dev/md0

mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=64 blocks, Stripe width=192 blocks
274718720 inodes, 1098853056 blocks
54942652 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
33535 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000, 550731776, 644972544

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
```**Step 8**. Modify fstab so the RAID mounts correctly.

**Step 9**. I then mounted the array and copy-pasted a file to it.  It was chugging along at 6.6mb/s.  That seemed rather slow, but if I can get it working then I'll be happy...

Some miscellaneous outputs at this point:

```
sudo gdisk -l /dev/md0
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: not present        #Is it weird that MBR and GPT are not present on md0?
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/md0: 8790824448 sectors, 4.1 TiB
Disk identifier (GUID): 26FAAE74-B26E-0AA4-0403-7098B786C50D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 200889822
Total free space is 8790824381 sectors (4.1 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
```
```
sudo gdisk -l /dev/sdb  #sdc, sdd, sde all showed similar results
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 2930277168 sectors, 1.4 TiB
Disk identifier (GUID): 763EE0E5-FDD0-475A-950B-7A1E8B402D63
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 2930277134
Total free space is 2020 sectors (1010.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      2930277128   1.4 TiB     FD00  
```**Step 10**. When I rebooted, my RAID failed to mount.  I tried a few commands and you can see the outputs below:

```
mount /dev/md0
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
``````
sudo gdisk -l /dev/md0  #Keep in mind I did this exact command BEFORE I  rebooted and it gave different results.  Now it looks like the md0 is a  regular 1.5tb partition, just like sdb1, sdc1, sdd1, sde1...
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.
Warning! One or more CRCs don't match. You should repair the disk!
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/md0: 8790824448 sectors, 4.1 TiB
Disk identifier (GUID): 763EE0E5-FDD0-475A-950B-7A1E8B402D63
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 2930277134
Total free space is 2020 sectors (1010.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      2930277128   1.4 TiB     FD00 
``````
sudo gdisk -l /dev/sdb  #and sdc, sdd, sde
*Showed the same thing it did before reboot
``````
sudo mdadm --stop /dev/md0
sudo mdadm -A /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: WARNING /dev/sdb1 and /dev/sdb appear to have very similar superblocks.
      If they are really different, please --zero the superblock on one
      If they are the same or overlap, please remove one from the
      DEVICE list in mdadm.conf.
#Each time I reboot, it gives the same error but possibly with a different drive (it originally gave sdc and sdc1 and then I rebooted and it gave sdb and sdb1.
``````
sudo gdisk -l /dev/sdb1
GPT fdisk (gdisk) version 0.5.1

NOTE: Write test failed with error number 2. It will be impossible to save
changes to this disk's partition table!

Problem opening /dev/sdb1 for reading! Error is 2

#Is this relevant or normal when trying to gdisk a partition?  
``````
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc[1] sdd[2] sde[3] sdb[0]
      4395412224 blocks level 5, 256k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
#I don't know why this shows sdb, sdc, sdd, and sde when I actually CREATED the RAID using sdb1, sdc1, sdd1, and sde1.
```**The stuff I find weird:**

1. sudo gdisk -l /dev/md0 before reboot showed no partition tables  present.  Now that command makes md0 look like a regular partition of a  1.5tb drive.

2. cat /proc/mdstat shows the RAID contains sdc[1] sdd[2] sde[3] sdb[0].   However, I created it with sdb1, sdc1, sdd1, sde1.  Searching online, I  found [this]("http://ubuntuforums.org/showthread.php?t=1689828&page=2") thread with similar issues.  In his, cat /proc/mdstat showed the  partitions, not the drives.  This seems like it could be a big part of  my problem - why does mdadm suddenly think the drive is the RAID, not  the partition!?

3. If I go into gparted before I rebooted, md0 showed a 4.1tb partition  called md0p1 with an ext3 file system.  When I reboot, before I "stop"  the mdadm, it shows as a 1.36tb partition with twice that amount of  space "unallocated" after the 1.36tb partition.  It seems like it knows  how big it is supposed to be but can't build itself...

Please help!
Thanks!
Mark

---

### Post by merill on 2011-04-27
Hello

My seagate drive is dead and i buy a **WD15EARS** to replace it.I use 4 raid5 array. I change the disk, format my os (on an usb key) to the newest version, i install mdadm and restart. All arrays are here.
I make 4 partitions in the EARS, same size, as i made for all my raid devices.
I add each partition to their array and all work very well.

Problem from chunck size?
Not-aligned partition?

good luck

(sorry for my poor english)

---

