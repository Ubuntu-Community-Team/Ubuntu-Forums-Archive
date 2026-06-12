---
title: "How to add 112 gb of unallocated space to a partition?"
date: 2011-10-15
forum: General Help
---

### Post by hreichgott on 2011-10-15
Hello,

I have Ubuntu 11.04 on partition sda1 and 11.10 on sda6, with a lot of unallocated space in between. I'd like to add the unallocated space to sda6, copy files over from sda1 to sda6, then eliminate sda1 entirely and give the space to sda6.

I can boot into either sda1 or sda6 and can run GParted on whichever partition I'm not currently booted into. (I also have a GParted live cd but it thinks all ext4 filesystems are corrupt.)

Here is the view in GParted right now. (attached)

---

### Post by wildmanne39 on 2011-10-15
Hi, here is  a great guide for partitions.

You will need to do it from a livecd and unmount the partitions.

Please be careful working with partitions and backup important data first.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
Thank you

---

### Post by hreichgott on 2011-10-16
Thank you for the help! I tried a regular Ubuntu live USB instead of the GParted bootable cd, and the version of GParted on the USB doesn't have a problem with ext4 file systems, which is good.

When I try to resize sda6 I get a warning message that the computer probably won't boot afterwards, because grub will look for the boot record in the old place, not the new place. How likely is this to actually happen, and if it happens, what do I do? I know just enough about grub to know that I have no business trying to modify it manually.

Both sda1 and sda6 are bootable (11.04 on sda1 and 11.10 on sda6).

---

### Post by wildmanne39 on 2011-10-16
Hi, it will happen if it said it will, I thought that was the case that is why I gave you the link and warning about partitons.

I am not an expert on reinstall grub from a livecd but here is a link to help.
[http://ubuntuforums.org/showthread.php?p=11352974#post11352974](http://ubuntuforums.org/showthread.php?p=11352974#post11352974)
Thank you

---

### Post by Quackers on 2011-10-16
Moving a bootable partition does carry a risk. I have moved them before and had a problem, but on the whole the moved partition usually boots without a problem.

If you intend to move files from sda1 to sda6 and then delete the sda1 partition you should check that your bios doesn't require a primary partition to boot from a drive. Some do.

---

### Post by oldfred on 2011-10-16
It is a bit more complex, but I prefer separate /mnt/data partition for data and link folders from the data partition into /home. Then you keep / (root) smaller and more efficient and can have data anywhere on system. Mine is usually on a different drive. 

Another alternative is just to move /home to sda1.

Either way you have to backup all your data in sda1.

---

### Post by hreichgott on 2011-10-16
Success, didn't disrupt the boot record/grub at all.
I kept the instructions though, thanks everyone.

Re. what to keep in what partition--I really prefer just having one big partition plus some swap space, but this dist-upgrade didn't seem to allow for installation into the same partition as 11.04 without disrupting data.

---

