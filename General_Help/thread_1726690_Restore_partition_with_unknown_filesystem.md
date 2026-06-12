---
title: "Restore partition with unknown filesystem"
date: 2011-04-11
forum: General Help
---

### Post by lin73 on 2011-04-11
Dear Forum members,

I need assistance with a particular issue. I recently did a clean install of 11.04 Beta, and I must have done something wrong with the mount points during installation, which resulted in me having a different home folder mount point or something. The old partition on which I have my home folder needed to be mounted manually. I did that once, and then upon reboot, I couldn't access the partition anymore. Disk Utility now shows the partition as "unknown filesystem".

The output of fdisk is as follows (if that helps at all):

[I]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3aa23aa1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       19456    74356852+   f  W95 Ext'd (LBA)
/dev/sda5   *       10200       19456    74356821    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3d24ac8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12865   103338081    7  HPFS/NTFS
/dev/sdb2           12866       30402   140859393    5  Extended
/dev/sdb5           29886       30402     4141056   82  Linux swap / Solaris
/dev/sdb6           12866       15297    19530752   83  Linux
**/dev/sdb7           15298       27323    96598813+  83  Linux**

Partition table entries are not in disk order[/I]

The damaged partition is sdb7.

On a side note, I tried using TestDisk to restore the partition, but I only created a DD image of the damaged partition, but now I'm stuck, as I'm not sure how to mount it, or if it's possible to retrieve files if I succeed in mounting the image.

Help much appreciated.

Regards

---

### Post by dabl on 2011-04-11
If you can boot into your OS, open a terminal and do these two things, and post the outputs, we can probably help.

```
cat /etc/fstab
```

```
sudo blkid -c /dev/null -o list
```

---

### Post by lin73 on 2011-04-11
[QUOTE=dabl]If you can boot into your OS, open a terminal and do these two things, and post the outputs, we can probably help.

```
cat /etc/fstab
``````
sudo blkid -c /dev/null -o list
```[/QUOTE]


Output of **cat /etc/fstab**:
UUID=4c0d90f9-5da3-439e-879e-0616bbcfde00 swap swap sw 0 0
UUID=6a901064-ca15-4017-8d46-527512d7b44e / ext4 defaults 0 1

Output of **sudo blkid -c /dev/null -o list**

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs             (not mounted)  8A08CC1808CC04E3
/dev/sda5  ntfs             (not mounted)  F0BC60BABC607CCA
/dev/sdb1  ntfs    New Volume (not mounted) 7038115938112020
/dev/sdb5  swap             <swap>         4c0d90f9-5da3-439e-879e-0616bbcfde00
/dev/sdb6  ext4             /              6a901064-ca15-4017-8d46-527512d7b44e

---

### Post by dabl on 2011-04-11
Yep, there's a problem with /dev/sdb7.  As a minimum, it has lost its UUID assignment.  I'm not sure how that happens -- it's never happened to me, and it's not a good thing.

As a stop-gap measure, it should be possible to set it up in /etc/fstab to mount automatically.  Do I understand that you intend this partition to be mounted on /home?  If that is the case, open your favorite text editor in "sudo" or root mode, and then open /etc/fstab for editing.  If you are using the Gnome desktop, I think you need to Alt-F2 "gksudo gedit" with no quote marks.

When you have /etc/fstab open for editing, add a new line like the red one below:

> UUID=4c0d90f9-5da3-439e-879e-0616bbcfde00 swap swap sw 0 0
UUID=6a901064-ca15-4017-8d46-527512d7b44e / ext4 defaults 0 1
[COLOR="Red"]**/dev/sdb7   /home   ext4   defaults  0  0**[/COLOR]

Save your edits, then shutdown and reboot your system, and it should come up with your /home partition as you intended.

HOWEVER ...

If it were my system, given these issues with /dev/sdb:

1. Unallocated blocks between 27323 and 29886
2. Partitions set up out of order
3. Mystery problem damaged the UUID assignment

I think I would back up my data, then boot my trusty [[COLOR="SeaGreen"]**Parted Magic**[/COLOR]](http://partedmagic.com/doku.php?id=downloads) USB stick, and re-partition that drive carefully, starting with making a new partition table on it.

---

### Post by lin73 on 2011-04-11
[QUOTE=dabl]Yep, there's a problem with /dev/sdb7.  As a minimum, it has lost its UUID assignment.  I'm not sure how that happens -- it's never happened to me, and it's not a good thing.

As a stop-gap measure, it should be possible to set it up in /etc/fstab to mount automatically.  Do I understand that you intend this partition to be mounted on /home?  If that is the case, open your favorite text editor in "sudo" or root mode, and then open /etc/fstab for editing.  If you are using the Gnome desktop, I think you need to Alt-F2 "gksudo gedit" with no quote marks.

When you have /etc/fstab open for editing, add a new line like the red one below:



Save your edits, then shutdown and reboot your system, and it should come up with your /home partition as you intended.

HOWEVER ...

If it were my system, given these issues with /dev/sdb:

1. Unallocated blocks between 27323 and 29886
2. Partitions set up out of order
3. Mystery problem damaged the UUID assignment

I think I would back up my data, then boot my trusty [[COLOR=SeaGreen]**Parted Magic**[/COLOR]]("http://partedmagic.com/doku.php?id=downloads") USB stick, and re-partition that drive carefully, starting with making a new partition table on it.[/QUOTE]

babl,

I don't think sdb7 can be mounted at all. I will try repartitioning, but does that mean that all data on sdb7 would be lost? Because at the time being, I cannot access this partition to back it up.

Thank you.

---

### Post by dabl on 2011-04-11
OK, let's try manually mounting it.  In a terminal do these:

```
sudo mkdir -p /mnt/sdb7
```

```
sudo mount -t ext4 /dev/sdb7 /mnt/sdb7
```

Now pop open your file manager and see if you can browse to /mnt/sdb7.  If so, you can back up the data to another device, I hope.  You are correct about repartitioning -- all data on that hard disk drive must be backed up before you repartition it, or you will lose it.

---

### Post by lin73 on 2011-04-12
[QUOTE=dabl]OK, let's try manually mounting it.  In a terminal do these:

```
sudo mkdir -p /mnt/sdb7
``````
sudo mount -t ext4 /dev/sdb7 /mnt/sdb7
```Now pop open your file manager and see if you can browse to /mnt/sdb7.  If so, you can back up the data to another device, I hope.  You are correct about repartitioning -- all data on that hard disk drive must be backed up before you repartition it, or you will lose it.[/QUOTE]

The manual mounting failed. I'll try repartitioning later.

Thank you for your time.

Rgds

---

### Post by grvsaxena419 on 2011-04-12
if the dd image you have created is correct you could try mounting the partition image file (i suppose you created a file of the partition) using mount -o loop 
if that could work you can backup you data .

---

