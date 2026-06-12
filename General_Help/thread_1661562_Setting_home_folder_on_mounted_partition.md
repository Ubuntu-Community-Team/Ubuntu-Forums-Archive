---
title: "Setting home folder on mounted partition"
date: 2011-01-06
forum: General Help
---

### Post by sletch on 2011-01-06
Hi-

Newbie here.  Most of the posts I've found while searching are about mounting a partition as a home folder, which I've done successfully but it's not quite what I'm trying to do.  I'm dual booting on a laptop with an 80gb hd. I've set up the partitions so windows xp has 20gig, ubuntu (edit: 11.4?) has 7 gigs, 3 gigs swap space, and the rest is formatted as FAT32 that I'm looking to use as shared space between the two OSes.  The ubuntu live install partition tool suggested (possibly demanded?) that the fat32 be mounted as /windows or /dos, and I chose the former.  Everything's running fine, both OSes see the partition, but I can't set my home folder to exist in this shared space.  

I've been in system > admin > users and groups- I try setting the home folder as /windows/home/chris.  (I had a home folder backed up that I have already copied to this location)  The dialog recognizes that there's a folder there already, asks if I want to use those new files or copy old ones.  I say use new files, and close the window.  Nothing changes though- in fact if I open users and groups immediately after, it's already reverted to /home/chris . I've tried changing from a different user account as well.  Any advice?

Thanks,

---

### Post by dcstar on 2011-01-07
> **sletch said:**
> Hi-

Newbie here.  Most of the posts I've found while searching are about mounting a partition as a home folder, which I've done successfully but it's not quite what I'm trying to do.  I'm dual booting on a laptop with an 80gb hd. I've set up the partitions so windows xp has 20gig, ubuntu (edit: 11.4?) has 7 gigs, 3 gigs swap space, and the rest is formatted as FAT32 that I'm looking to use as shared space between the two OSes.  The ubuntu live install partition tool suggested (possibly demanded?) that the fat32 be mounted as /windows or /dos, and I chose the former.  Everything's running fine, both OSes see the partition, but I can't set my home folder to exist in this shared space.  

I've been in system > admin > users and groups- I try setting the home folder as /windows/home/chris.  (I had a home folder backed up that I have already copied to this location)  The dialog recognizes that there's a folder there already, asks if I want to use those new files or copy old ones.  I say use new files, and close the window.  Nothing changes though- in fact if I open users and groups immediately after, it's already reverted to /home/chris . I've tried changing from a different user account as well.  Any advice?

Thanks,

You **cannot** put Linux system folders - like /home - on rubbish non-Linux file systems.

---

### Post by KeyserSoze93 on 2011-01-07
> **dcstar said:**
> You **cannot** put Linux system folders - like /home - on rubbish non-Linux file systems.

You can, however, put your Windows "My Documents" folder on an ext2/3 partition.

On my dual booting box, the Windows' E:/ drive is the same as the Linux /home partition, using the Ext3IFS filesystem drivers.

I simply right clicked the "My Documents" icon and set the path to E:/theo, and I have an almost seamless transition between the two systems.

---

### Post by oldfred on 2011-01-07
I suggest you use NTFS as it has journaling and can save files over 4GB. Use FAT only for small devices like flash or where you have to for compatibility with another device like your camera.

Windows formats do not support ownership and permissions like all Linux formats do. That is part of the improved security of Linux over Windows. So you cannot use any windows formats for Linux system partitions. But you can use a NTFS partition for a shared data partition.

You should not write into foreign systems, use the shared for any writing of common data. You can read from the windows system partition and I do write into it with Ubuntu only to make repairs. Ubuntu will show all the hidden system files & folders in windows and it is too easy to accidentally delete or modify something in windows if you have full write capability.

I use the NTFS partition for my Firefox & Thunderbird profiles so have all the same email & bookmarks in both systems. When I was first starting in Ubuntu and trying to learn it was frustrating when spouse wanted to check email or internet and it was only in windows. Once set up with shared profiles we did not boot into XP much at all.

---

