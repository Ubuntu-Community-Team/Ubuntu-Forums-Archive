---
title: "How To Move Unallocated Space From Ubuntu -&gt; Windows"
date: 2011-10-17
forum: General Help
---

### Post by demonboy on 2011-10-17
Hi,

I have this hard drive structure, which divides Windows 7 (partitioned to C and D drives) and Ubuntu 11.04 (two partitions but one, sda5, hardly used).

[IMG]http://farm7.static.flickr.com/6229/6254483391_1e322327d7_b.jpg[/IMG]

I'd like to be able to reduce sda5 and move that space over to Windows. However if I move the left slider it makes Unallocated space. If then then make this either ntfs or ext4 and reduce that, it adds in an annoying little extra partition to the left of my newly reduced ntfs, which I can't get rid of. When I try and do anything with this it says 'Could not add this operation to the list - a partition cannot have a length of -2048 sectors.

What is the trick of reducing my Ubuntu partition, sda5, and adding the extra space to sda2 and sda3?

---

### Post by coffeecat on 2011-10-17
You have three primary partitions and one extended partition in which you have three logical partitions. You are trying to move some of the space used by one logical partition to a primary partition. The way to do this is to:

[list=1)
[*] - Shrink sda5 from the left.

[*] - Move the left boundary of the extended sda4 partition so that the unallocated space comes before the left edge of sda4.

[*] - Enlarge the sda3 partition to include the freed space.[/list]

You cannot add the freed space to sda2 unless you move sda3 to the right which will take some time.

A couple of other points:

You need to do the shrinking of sda5 and sda4 with Gparted in the live CD. And you will need to right-click on the swap partition (sda7) and choose "swapoff" before you will be able to resize sda4.

If your Windows version is Vista or Windows 7, I suggest you use Windows own Disk Management tool for resizing the sda3 NTFS partition.

---

### Post by demonboy on 2011-10-17
Thank you very much for the quick response. I am using Gparted on a memory stick so I am in neither OS. I guess this is the same as using the Live disk Just finishing something off and will attempt your suggestion in a few minutes. Thank you.

---

### Post by coffeecat on 2011-10-17
By the way - I'm sure you know this - you are going to do a lot of partition resizing. Make sure you've backed up everything. You shouold be fine, but sometimes things can go wrong.

And, yes, a live USB of Ubuntu is fine.

---

### Post by demonboy on 2011-10-17
Worked!

Thank you, can't believe it was that simple.

---

### Post by coffeecat on 2011-10-18
You sound surprised! :) I'm glad it worked for you.

---

