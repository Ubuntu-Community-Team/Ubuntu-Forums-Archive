---
title: "Windows partition not recognized in Gparted live"
date: 2010-02-14
forum: General Help
---

### Post by Mr Nemo on 2010-02-14
I'm trying to add more memory to Ubuntu from my windows partition, but Gparted doesn't seem to recognize the windows partiton. I've done it before using the gparted live cd, so i don't know why it wont recognize the partition. Is there some way to mount it so I can move space around?

---

### Post by Mr Nemo on 2010-02-14
bump

---

### Post by ajgreeny on 2010-02-14
> **Mr Nemo said:**
> I'm trying to add more memory to Ubuntu from my windows partition, but Gparted doesn't seem to recognize the windows partiton. I've done it before using the gparted live cd, so i don't know why it wont recognize the partition. Is there some way to mount it so I can move space around?
I assume you mean you want to add more disk space to a wubi install of ubuntu from within windows, and I am pretty sure that can be done.  have a good read through the wubiguide [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) and you may get an answer.  Never having used wubi, I can't be more helpful.

---

### Post by Mr Nemo on 2010-02-14
Not wubi, dual boot with win vista and ubuntu. I haven't really used gparted that much, but when it reads my windows partition it says i have less free space than I really do. And it wont let me make changes. I didnt have a problem last time. Any suggestions?

---

### Post by ironclaw on 2010-02-14
Try to post a screenshot of gparted and the output of
```
sudo fdisk -l
```to list your partitions.

Right now, I can only think of 2 possible reasons:
1) The partition is mounted
2) The file system is unclean (e.g., hard reboot last time the NTFS partition was mounted)

But then, gparted should show an option for unmounting the partition if the problem is (1) and it should show an error dialog if the problem is (2)... So I'm not sure.

---

### Post by Mr Nemo on 2010-02-14
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d702ecc

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
/dev/sda2             192       15490   122880000    7  HPFS/NTFS
/dev/sda3           15491       19457    31864927+   5  Extended
/dev/sda5           15491       19266    30330688+  83  Linux
/dev/sda6           19267       19457     1534176   82  Linux swap / Solaris

```
There was an error message when I tried to move memory around. I can't really remember what it said, I think it was some reference number.

---

### Post by ajgreeny on 2010-02-15
The trouble seems to be your sda1, which is an unknown filesystem of about 1.5GB, and should be ntfs, I assume as it is the boot flagged partition, ie probably windows.

I'm afraid I am now out of my depth, and I think you have a problem here which I will have to leave to others.

---

### Post by plucky on 2010-02-15
> There was an error message when I tried to move memory around. I can't really remember what it said, I think it was some reference number.

**First Backup your data**

I would recommend you use Windows Vista disk management tools to shrink your NTFS partition as it has been reported that you could break Vista if you use Gparted to resize the windows partition.

Defragment the partition before shrinking from within vista.

Once you have shrunk the vista partition and there is un-allocated space on your disk,you can then use gparted on the Live CD to move/resize your Ubuntu partition.

From to setup of your disk,your linux partition is inside the extended partition,so you have to resize the extended partition before you resize your linux partition.
Also make sure the swap file is un-mounted before you try to resize the partition.


Good Luck

---

### Post by Mr Nemo on 2010-02-15
So instead of using windows disk management I used a different windows partitioner and now I can't boot windows (I was fully aware this might happen), but I successfully grew my ubuntu partition so alls well. Is there someway to save my windows partition or is that a lost cause?

*Windows disk management was gonna make me do a bunch of stuff i didnt want to deal with, so I didnt bother*

---

### Post by ironclaw on 2010-02-15
What boot loader do you have - do you have GRUB or do have the Windows boot loader? Can you boot into Ubuntu?

Also, did you resize the Windows partition from within Windows?

---

### Post by Mr Nemo on 2010-02-15
I have grub, and yes I can boot into Ubuntu. I used partitionmagic which is a windows program, but it made the changes to the partition when I restarted the computer. It seems something happened to the windows boot partition.

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d702ecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192        8942    70286387+   7  HPFS/NTFS
/dev/sda3           15491       19457    31864927+   f  W95 Ext'd (LBA)
/dev/sda5           15491       19266    30330688+  83  Linux
/dev/sda6           19267       19457     1534176   82  Linux swap / Solaris

```

---

### Post by ironclaw on 2010-02-15
Can you mount the NTFS partition (i.e., sda2) in Ubuntu?

What's strange is that fdisk only shows that the NTFS partition has been shrunk, but according to it everything else is still the same size.

Do you know what is in sda1?

---

### Post by Mr Nemo on 2010-02-15
I'm pretty sure sda1 is the windows boot partition, which seems to have been corrupted in some way. 

Is that the windows MBR, and can I fix it with bootitng or some other program? Yes, I can mount sda2.

---

### Post by Mark Phelps on 2010-02-16
You will need to locate, download, and burn a repair CD image from the NeoSmart Technology forums.

Then, you will need to boot from that CD and run startup repair several times, most probably, three times.

Then, if you get that working, you will have to reinstall GRUB.

This is all because you "didn't want to bother" with using the right tool for the job.

---

### Post by Mr Nemo on 2010-02-16
What does that 'partition 1 does not end in cylindar boundary' mean?

---

