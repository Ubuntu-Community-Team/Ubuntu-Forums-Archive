---
title: "quad-boot troubles"
date: 2010-03-15
forum: General Help
---

### Post by Scarfnoogan on 2010-03-15
Good morning all, I've been running Karmic for a couple weeks now and it's great, but as my ADD kicks in, I realize that I would like to try other flavours.
 
I've currently got my hard drive partitioned for Karmic, XP, Mint, and swap, however when I try to add another Xubuntu, it says I have the max partitions.
 
I've read the guides and such, and it seems that with an extended partition I can have more OS's, but I can't seem to increase the size of my swap partition(extended) or make a new one.
 
is there a way to do it without erasing the entire drive and starting from scratch?
 
Thank you

---

### Post by mike555 on 2010-03-15
if you have unused space you could just delete the swap for now and make a extended partition , then a new swap area ..... but you would need to change each operating system to use that swap area........... probably better to get a new harddrive and start over...... you could do as I do on my "test" computer and install grub to the partition you install linux to and use a different boot loader like GAG to load them .......but in any case make a large extended partition (except of course for Windows)

---

### Post by Scarfnoogan on 2010-03-15
thanks, that sounds like a good place to start

---

### Post by Arand on 2010-03-15
What is the current partition layout, do you already have an extended partition, is the swap a logical?

(output from "sudo fdisk -l" would help)
- Arand

---

### Post by Scarfnoogan on 2010-03-16
here's my fdisk

```
Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33323331

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       35944   288720148+  83  Linux
/dev/sdb2           41044       47417    51199155    7  HPFS/NTFS
/dev/sdb3           47418       48641     9831780    5  Extended
/dev/sdb4   *       35945       41043    40957717+  83  Linux
/dev/sdb5           47418       48641     9831748+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Arand on 2010-03-16
I'm not completely sure it's the best way, but what I would do in this case is:

DISCLAIMER: I would soothe myself with a nice cake if something should go wrong, make sure you have an equally appropriate response ready if something goes haywire.

[LIST=1]
[*]Backup all important data, clone partitions, bootrecords, partition tables, etc.

[*]Remove the current swap & extended partition

[*]Shrink sdb1 and create an empty extended partition behind it (sufficiently large for a root Xubuntu, and swap partition)

[*]Install Xubuntu using the "use largest continuous free space"-option (this should put it inside the new extended partition, if not, use manual partitioning and make it so)

[*]In the final install screen, choose advanced and set the bootloader to be installed to the partition you are installing Xubuntu to (and not the mbr), this if you want to keep the current bootloader you are using, which I'm guessing is already setup nicely.

[*]Still from the liveCD, use```
sudo blkid
```to find the UUID of the new swap partition

[*]Edit the /etc/fstab of both existing linux drives to use this UUID for their swap

[*]boot into the distro which currently hosts your bootloader (I'm guessing that'd be whatever is on sdb4)

[*]Run```
sudo update-grub
```Which should hopefully find your new install with associated kernels as well.

[*]If all went well, everything should work

[*] If you want, you could reclaim the 9GB at the end of the drive by resizing your NTFS partition, it's not completely safe since windows dislikes having it's partitions shoved around, but after a chkdsk (automatically scheduled by gparted) it should be fine.
[/LIST]

- Arand

---

### Post by Scarfnoogan on 2010-03-16
Awesome, that will be tonights project :D
 
Actually, one more question, I've read that I don't need a swap partition if I have more than 2G of ram, I have 4...how would I go about not creating a swap(it's been a while since I've been in the install program, so forgive me if it's right there staring at me)

---

