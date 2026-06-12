---
title: "moving the swap partition"
date: 2006-01-23
forum: General Help
---

### Post by Lunixfanboy on 2006-01-23
Depending upon how your partitions BEFORE the swap partition are numbered, yes, you can most certainly move the swap partition and delete the extended IF you have nothing else in the extended partition. If, as an example, you only have Ubuntu on /dev/hda1, you could remove the extended partition (and all inside it) and make a primary partition which could serve as swap in the free space (/dev/hda3 as an example). You would first have to deactivate the swap file currently in use, then using a disk partition tool such as cfdisk, fdisk, sfdisk, qtparted, gtparted, to remove the extended and its contents then add a new primary partition of type swap (82). Then, use the command mkswap to designate the newly created partition as swap space. Finally, edit the fstab file to indicate where the new swap file is located (edit the swap line to point to the new partition) and activate it using swapon command. The only trouble would be if you have (as I do) a swap file in amongst  other partitions, and removing it would cause all other partitions to be renumbered, causing havoc with the bootloader. If you need specific steps, please ask.

---

### Post by smaller on 2006-01-23
I have a linux-swap partion which is inside an extended partition. I would like to move the linux-swap to a bit of unallocated space on the same harddisk and preferably out of the extended partition.

Can I just remove both partitions and create a new swap space or will this get me in to trouble? I don't want to make my main partition unbootable due to these changes.

---

### Post by smaller on 2006-01-24
Thanks for your response Lunixfanboy. I do have other partitions, so you are right, if some of them get renumbered grub will be messed up. But I ran into these kinds of problems before and they're relatively easy to solve. I'll give it a try tonight.

[LIST=1]
[*]swapoff
[*]delete the old partitions (swap and extended)
[*]create the new swap partition
[*]mkswap
[*]edit /etc/fstab 
[*]swapon
[/LIST]

---

