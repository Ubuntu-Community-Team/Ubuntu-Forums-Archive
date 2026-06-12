---
title: "Extending linux (ext4) partition"
date: 2011-05-29
forum: General Help
---

### Post by Theadamlt on 2011-05-29
Hi all,

I have tried to expand my EXT4 linux partition, without success.

I have Windows 7 and ubuntu installed, so i shrinked the Windows partition, so that i now have 60 GB unallocated space. If i open up Gparted and rightclick my Ubuntu partition, i can't select the resize/move, since its greyed out. So i tried to boot the Gparted live disk, and do the same. This time, the resize/move field is not greyed out, BUT i can only shrink the partition. The up arrow is just greyed out. Does anyone have a solution?

Thank you in advice

Adam

---

### Post by drs305 on 2011-05-29
I created a thread about how to do this. Here is the link:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

It mentions a couple of 'gotchas' such as making sure the swap partition is unmounted (even on a LiveCD).

---

### Post by cmcanulty on 2011-05-29
You have to do it in live CD or it is mounted and won't work

---

### Post by VanR on 2011-05-29
I had this problem. Even in Live CD I had to turn swap off. Swap was mounted and I couldn't do anything to the partitions without unmounting swap.

---

### Post by cmcanulty on 2011-05-29
unmounting swap shouldn't cause a problem

---

### Post by Theadamlt on 2011-05-29
Hmm... I booted the LiveCD and maked sure that any partitions wasn't mounted, but the up arrow was still greyed out... Am i doing anything wrong?

Thank you in advance

Adam

---

### Post by drs305 on 2011-05-29
> **Theadamlt said:**
> Hmm... I booted the LiveCD and maked sure that any partitions wasn't mounted, but the up arrow was still greyed out... Am i doing anything wrong?

Thank you in advance

Adam

Please take a snapshot of gparted and post it in a thumbnail so we can see what you are looking at. Did you look through the thread I linked? Are you trying to expand a logical partition before expanding it's container (the extended partition)? 

A picture's worth a ......

---

### Post by Theadamlt on 2011-05-30
Okay as soon as i get home from school, i'll take screenshot

---

### Post by Theadamlt on 2011-05-30
[http://imageshack.us/photo/my-images/714/imag0074zi.jpg/](http://imageshack.us/photo/my-images/714/imag0074zi.jpg/)

[http://imageshack.us/photo/my-images/8/imag0075l.jpg/](http://imageshack.us/photo/my-images/8/imag0075l.jpg/)

Here is the screenshots...

---

### Post by dandnsmith on 2011-05-30
It's ovbious what the problem is, from the images -
- the unallocated space is at the far end of the disk from the ext4 filesystem
- the linux stuff is in an extended partition, and occupies it all
- 2 primary partitions follow the extended partition.

You'd have to move the 2 primary partitions (which will probably end with Windows not working - depends on details of boot setup),
then expand the extended partition to include the spare space,
then move the swap partition to the end of the extended partition
finally expand the ext4 partition

HTH

---

### Post by Theadamlt on 2011-05-30
Okay, but how do i move the partitions?

---

### Post by Theadamlt on 2011-05-30
How do i move the partitions? And will i break the windows partition?

---

### Post by Theadamlt on 2011-06-01
Nevermind, i just formated my hdd and did a clean install :)

But thanks for the help anyway.

Adam

---

### Post by glene77is on 2011-06-01
> **Theadamlt said:**
> Nevermind, i just formated my hdd and did a clean install :)

But thanks for the help anyway.

Adam

Thea,
BEST IDEA so far !!!   

I have done the clean install on bunches of computers, just to clear up problems. 
M$-XP installed first,   into a  sda1 Primary partition.

Booted the Parted-Magic Live-CD to: 
(1) shrink XP down to 10 G, on the left end.
(2) create the 1 Gig Swap on the far right end.
 (3) create a large Extended partition  in the middle.
(4) creating several 10 G partitions for several Linux OS  and  Data areas, inside the Extended partition. 
(5) install Ubuntu, with Grub2, and a new MBR. 

Always works.
Remember to keep your "Created Data" in a separate partition, 
and use a simple Filemanager copy  or Grsync for backup to external HD. 

buena suerte,

---

