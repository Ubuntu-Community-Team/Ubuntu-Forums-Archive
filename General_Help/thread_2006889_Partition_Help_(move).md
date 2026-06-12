---
title: "Partition Help (move)"
date: 2012-06-19
forum: General Help
---

### Post by wagb278 on 2012-06-19
I have a drive that swap partition is in the middle and I want to move that to the end so I can extend the size of the partition before it. 

See the attached screen-shot (if I did that correctly)

The 13 GB partition is my Ubuntu boot location and the 105 GB partition is a mounted data partition (mount point = /data). My /home mount point is on another drive. Notice the unused 129 GB at the end.  I would like to locate that at the end of the data partition and then extend data to use the extra 129 GB. 

Is there a way to do this?  All that comes to mind is to image the boot partition and /data partition with CloneZilla (or whatever) and then wipe the drive and restore the images.  Is there less possibly catastrophic way to accomplish this.  

I am running 10.04 LTS

---

### Post by wilee-nilee on 2012-06-19
Post a screenshot of gparted and identify the partitions by name and what you want done.

---

### Post by oldfred on 2012-06-20
I think you just need gparted to expand the extended partition to include all the unallocated, and then move swap to the end of the extended partition. That should not change UUID, but be prepared to edit fstab with new UUID if it gives errors on booting. You should not have to reinstall grub2's boot loader as you will not move that partition.

Always best to use liveCD to be sure all partitions are unmounted, but liveCD will probably mount swap to speed things up a bit, so click on swap in gparted and right click swap off.

---

### Post by Bucky Ball on 2012-06-20
> **oldfred said:**
> 

Always best to use liveCD to be sure all partitions are unmounted, but liveCD will probably mount swap to speed things up a bit, so click on swap in gparted and right click swap off.

+1.

Personally I'd kill the extended which only has swap in it, expand the partition at the beginning of the drive (in my understanding that's the one in question) then create an extended partition with whatever free space is left and the /swap at the end of that, as suggested by oldfred.

---

### Post by wagb278 on 2012-06-20
Thanks for the replies.

wilee-nilee - Attached should be a screen-shot of this drive (sdb) captured using gparted.

What I want to do is extend the /dev/sdb2 partition (mount point "/data") to include the unallocated space (119 GB) at the end of the drive. And move the swap to the end of this drive.

The swap in the middle makes me think I can't just increase the size of /dev/sdb2; am I wrong there?  I don't know what I was thinking putting swap where it is. 

For reference my other drive (dev/sda) is shown in the second screen-shot and I intend to expand /dev/sda2 on that to include the unallocated space on that drive, but that should be an easy expand action in gparted because the swap is at the end. 

If interested; the first partition on each drive are my boot partitions. sda1 has Ubuntu 08.04 LTS and sdb1 has Ubuntu 10.04 LTS. As a new LTS version is released I replace the oldest with the new one; each using the single /home (sda2) partition.  The "/data" partition (sdb2) is accessible over my home LAN from other computers and is where I save backup copies of files. As you can see that partition is filling up and I want it to now include the unallocated space on this drive. 

Thanks for the assist everyone.  If more info is needed, just ask.

---

### Post by oldfred on 2012-06-20
You could do the way I suggested and then shrink the extended, but Bucky Ball's way just may be quicker. If not adverse to updating fstab with new UUID it will probably be quicker also.

#To find new UUID.
sudo blkid
#Change UUID from old swap to UUID of new swap:
gksudo gedit /etc/fstab

---

### Post by wagb278 on 2012-06-22
After saving partition image files using CloneZilla and downloading the latest Parted ISO (my copy of Parted Live-CD was many years old). 

I followed oldfred's suggestion. This is what I did:
[LIST=1]
[*]Resize Extended to consume all Unallocated
[*]Move Swap to the end of the now larger Extended
[*]Reduce Extended to include only the Swap (from the front)
[*]Expand sdb2 to include the new Unallocated space in front of Expanded
[*]Apply those changes - All OK
[/LIST]

Ubuntu booted just fine; but the first thing I did was to compare results of "blkid" with contents of /etc/fstab and no UUID values were affected by these actions. 

Thanks for the help to all, and in particular oldfred.

---

