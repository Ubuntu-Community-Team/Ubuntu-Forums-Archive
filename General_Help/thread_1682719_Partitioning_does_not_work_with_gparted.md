---
title: "Partitioning does not work with gparted"
date: 2011-02-06
forum: General Help
---

### Post by Krabby.Linux on 2011-02-06
Hey,

simple Question ... big Problem ;-). (See Attached Image)

I have available Space and i want this Space on my Ubuntu. That Means that l want the unallocated 92.77GB on my /dev/sda8 (ext4)?!?!?.

But I cant Resize the Partition ... What do I have to do ? I tried it using Ubuntu on my USB. But it was the same.... Do I have to unmount something ?

Thanks

---

### Post by [Snc] on 2011-02-06
You can create another EXT partition in the unallocated space and then mount it in Ubuntu
(maybe, use it as a media partition; mp3, avi, backups,...)

You can click on the unallocated space (to select it) and right click and in the menu select "*New*" and then "*Format to*"...

---

### Post by Krabby.Linux on 2011-02-06
I want a bigger Ubuntu Partition. Isnt that possible?

---

### Post by [Snc] on 2011-02-06
Hmm :) i would be precocious with that thought, that would mean, that you would have to move your NTFS partition to the right .... You can do that with right clicking on the NTFS partition, select "Resize/Move" and simply dragging the partition to the right.

But be warned :) I did the same thing a few days ago and it took aaaaaaaageeeeeees (26h in my case of a 1Tb drive) ...

Besides, please before doing anything, make sure, that your windows will still be bootable after that operation! (I cant help you here...)

---

### Post by mcduck on 2011-02-06
Looks like a bit rather tricky thing to do with your current partitioning scheme.

- The free space must be next to the partition where you want to add it.

- sda8 is a logical partiton inside an extended partition (sda4), while the free space is outside it.

So, you'll have to first grow /dev/sda4 to use the free space, then move sda6 to the beginning of the sda4 and *then* you'd be able to grow sda8 to use the free space.

---

### Post by Krabby.Linux on 2011-02-06
Hey, thanks for the replies but i cant resize /dev/sda4 how do i Do that?

---

### Post by oldfred on 2011-02-06
Whatever you do you first have to move the start of the extended partition left to include the unallocated.

You have to use a liveCD so your partitions are not mounted. LiveCD often mount swap automatically so you may still have to click on the swap partition and swapoff to unmount it. You have two so you may have to swapoff both.

I would just create a new partition and move /home into it. I usually recommend only 10 to 20GB for / when you have all your data in /home. Or you can leave /home and just move the data folders like Music, Documents, Video etc to a /data partition.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

To move /home uses rsync  (create mount may be missinig)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.

---

### Post by mcduck on 2011-02-06
> **Krabby.Linux said:**
> Hey, thanks for the replies but i cant resize /dev/sda4 how do i Do that?

All partitions inside sda4 must be unmounted before you can resize it. The Ubuntu live-CD will automatically use any swap partitions it finds, and you have two swaps inside sda4, so you must unmount them first.

```
sudo swapoff -a
```

---

### Post by Krabby.Linux on 2011-02-10
Everything went fine. Thanks.

Just Grub was having some problems. Had to install it again and now eveyrthing is like i wanted to.
Thank you

---

