---
title: "Cannot edit Ubuntu partition size."
date: 2009-07-19
forum: General Help
---

### Post by GUNBLADE99 on 2009-07-19
Hi, I already have read through stickies and have an idea how to edit the size of the partitions. It doesn't seem to work for me. The move/resize and unmount options just aren't available to me on my hdd when I click on it.. I'm simply trying to just get 10 or so gigs for my ubuntu to install updates and some software and be able to save a few files here and there for work.

Right now, I have no space and can't even access the internet or install updates.

Here is a picture of what it currently looks like. Seems very messy to me. 
[IMG]http://i4.photobucket.com/albums/y125/GUNBLADE99/Screenshot--dev-sda-GParted.png[/IMG]

---

### Post by michy99 on 2009-07-19
First you need to shrink sda2 to make some room. You only need one swap partition, so delete sda4. sda5 and sda6 are logical partitions inside the extended partition sda3, so you have to expand sda3 and then expand sda5. You have to do this from a Live CD because you can't change a partition while it is mounted. Also the swap has to be off.

If you expand sda5 to the left, you will have to edit your fstab file if it uses UUID because the UUID will change. If it uses /dev/sda5 designation you don't have to worry about it.

---

### Post by Wickd on 2009-07-19
Hi there

You wont be able to edit your UBUNTu partition if you booted into UBUntu from your HD.

You will need to do this from your live cd. The unmount option will then be available (if the partition is indeed mounted).

You can then proceed to shrink your partition size or resize it or woteva :)

Cheers!

---

### Post by Sidewinder1 on 2009-07-19
It appears to me that you'll need to shrink sda2, your NTFS partition and create a new ext3 partition in that newly created space. Make absolutely certain that you run Windoze defrag (probably your C:\) at least once, twice wouldn't hurt if it hasn't been defragged in a long time, immediately before shrinking/resizing with gparted.
Making a back-up of your important data on the NTFS would be a good isea too.
Not sure why you have 2 "Swap partitions", only one is needed and it should be 1.5 to 2 times your amount of installed RAM.
That should get you headed in the right direction.
I've only used gparted a few times (all successfully, thank the spirits) so I'll let someone more knolegable than I chime in with exact step by step instructions...
HTH, 
Side

---

### Post by GUNBLADE99 on 2009-07-19
Thanks all so far. I got my hands full, but will try it out in a short while. I just need to get the live cd for the partition editor software.

---

