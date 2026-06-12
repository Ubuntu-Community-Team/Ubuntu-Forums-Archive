---
title: "Partition Juggling"
date: 2010-08-10
forum: General Help
---

### Post by cheshirekow on 2010-08-10
My computer is now about a month old. It (of course) came preinstalled with windows 7. I kept it in case I needed it but it looks like I probably wont after all and I think I'm ready to drop it's bloat from my small hard-disk (256GB is small these days... *sheds tear*).

When I installed 10.04 I had some problems so I ended up installing 9.04 as well so that I could have something to boot into, mount the other partition, and edit things.

So... this is what my hard drive looks like in GParted:
```

Partition       File System    Label            Note
/dev/sda1       fat16          DellUtility      (ew..)
/dev/sda2       ntfs           RECOVERY         (windows 7 boot)
/dev/sda3       ntfs           OS               (windows 7 actual)
unallocated
/dev/sda4       extended
   /dev/sda5    ext3                            (Ubuntu 9.04)
   /dev/sda7    ext4                            (Ubuntu 10.04)
   /dev/sda6    linux-swap                      (swap... duh)

```

Now that I'm comfortable with all the quirks of 10.04, and have found all the drivers I need in order to make my Dell behave, I want to get rid of windows 7 and Ubuntu 9.04. I thought I could just delete partitions 1-3, 5 and then resize partition 7 to fill up the space, but evidently this is not possible because partition 7 is on an extended partition. Is there an easy way to get rid of the 4 unneeded partitions and fill the drive with just 10.04... or do I need to reinstall everything?

---

### Post by quixote on 2010-08-12
No, you don't need to reinstall everything.  But it's going to be rather tedious anyway :(.  I'm assuming you're using gparted.

Assuming you're sure you really want to get rid of all the non-Lucid partitions, this is what I would suggest for the goal: a root partition for Lucid of 10 - 15 GB.  A swap partition which is 1.5 -2 times system RAM.  (E.g. for a system with 2GB memory, 3GB swap is big enough.) And the rest all in a home partition. I would also suggest applying the steps as you go through them rather than stacking up all of them.

Boot from a liveCD or liveUSB.

You don't say how big sda1, 2, and 3 are.  Delete enough so you have space for your future root partition.  I don't remember whether at this point you should copy sda7(Lucid) partition to the free space, or format it first.  Try copy, and see if it gives you the free space at the beginning of the drive as a choice.  (Otherwise format first by selecting "new", format ext4, and select mount point: /)    Copy sda7 to the beginning of the drive, and then expand the partition to the size you want.

At this point, I would close gparted and reboot the computer.  It will boot into sda7.  Run sudo update-grub and it will find the first partition with the copy on it.  Reboot, only this time select the first partition in grub.  Check to make sure it boots.  If all is well, then go on with the rest:

Boot with live cd, format a swap partition of the desired size after /.  Delete all the other partitions and format the space as ext4 and be careful to choose mount point: /home.  You could also, of course, designate it extended and have /home as a logical partition.

The advantage to having /home separate is that you can reinstall the system in / without losing any of your configurations saved in /home.  The advantage to having home as the last partition is that if you decide to make a new partition, there can be less fighting with gparted involved.

---

### Post by cheshirekow on 2010-08-12
Actually after some searching I found something that I think worked. What I did was as follows. 

1. Boot into live cd (9.04 install for me)
2. Run GParted and delete partitions 0,1,2
3. Create two new partitions in the newly freed space (120GB ext4 and 5GB swap)
4. Copy file system from old partition to new partition
```
 sudo -i
mkdir /mnt/new
mkdir /mnt/old
mount /dev/sda1 /mnt/new
mount /dev/sda7 /mnt/old
cp -ax /mnt/old/* /mnt/new/
exit

```
5. find the UUIDs of the new partitions
```

sudo blkid

```
6. edit fstab replacing UUIDs for "/" and "swap" to the UUIDs of the
```
 new partitions
gksudo gedit /mnt/new/etc/fstab

```
7. reboot and remove install cd
```

sudo shutdown -r now

```
8. boot as normal into sda7
9. update grub2 so it sees the OS on the new partition
```

sudo update-grub

```
10. reboot
```

sudo shutdown -r now
[code]
(for steps 8-10 I suppose I could have just booted into sda1 by editing the command for boot while in the grub2 menu, but I didn't think of that at the time)
11. when in grub, select the os on the new partition (sda1)
12. once booted into OS on sda1 then reinstall grub2 to MBR
[code]
sudo update-grub
sudo grub-setup /dev/sda

```
12. reboot again
```

sudo shutdown -r now

```

At this point the grub that loads on boot is the one on sda1, aka partition 0 (or is it 1 now in grub 2? the first one in any case). Now I can run gparted and delete the whole extended partition, and then expand my primary partition (actually, I guess I have to move swap to the end of the disk first... but that's not too hard). For now, I'll leave it like this until I'm confident nothing is too screwed up.

I like your idea of mounting /home separately to avoid issues with partition juggling, but this seems to have worked out OK too.

---

