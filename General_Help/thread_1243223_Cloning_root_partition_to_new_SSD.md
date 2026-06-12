---
title: "Cloning root partition to new SSD"
date: 2009-08-18
forum: General Help
---

### Post by kubuntuuser on 2009-08-18
Hi Experts,
I'm hoping someone can help me out cloning my root partition to a my new crucial 64 GB SSD.

I currently have a 1TB SATAII hard drive split up as follows
/ = 30 gig (ext3)
swap = 4 gig
/home = everything else 700+ gig (ext3)

I'd prefer not to re-install Ubuntu and was hoping to clone my root partition using Clonezilla and put this on the new SSD. As far as I'm aware, this is the easy bit.

However I have a number of questions regarding the processes after the partition has been cloned and placed on the SSD and more general questions about maximising the life out of my new SSD.

I can imagine that a number of files will need to be updated to ensure that /home is still mounted at boot and that the new / partition becomes the partition that is booted from instead of the old root partition. I'm thinking the grub.conf and /etc/fstab are the likely files that would need to be updated?

Is this assumption correct or will other files need updating too? Can anyone provide an example of the types of changes that would be required?

To ensure that I maximize the life of my SSD I've heard that you should use an non-journalling filesystem like ext-2 to prevent re-writes to the same area of the disk thus shortening the life of an SSD? How true is this, does it really matter if I leave it mounted as ext3 which is how it will be cloned?

I'm not too concerned with journalling the root partition as long as the /home partition where my data is stored continues to be journalled as this is where I'm worried about data corruption.

I'd also like to create a dedicated /var partition for log files (again to increase the life of my SSD) back on the SATA drive in the place of the old root partition. Does anyone have any recommendations on sizes? Also what will I need to do to ensure that this new partition is mounted at boot? How do I reclaim the space used by the original var area that would be taken up by the old var area

I know there is a lot of questions in this post but would appreciate any help to make this as pain-free as possible.

Thanks in advance guys

---

### Post by Grenage on 2009-08-18
> To ensure that I maximize the life of my SSD

Worry not, the current SSD's can **constantly** write across the whole drive for about three fears before failure.

---

### Post by drewster1829 on 2010-06-05
I know this is an old thread, but in case anyone else stumbles across this, here are the instructions I used:[URL="http://ubuntuforums.org/showthread.php?t=1492089"]
http://ubuntuforums.org/showthread.php?t=1492089[/URL]

---

