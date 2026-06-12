---
title: "Gparted Partition Problem"
date: 2011-05-12
forum: General Help
---

### Post by Tanasqui on 2011-05-12
Hello friends, 
  My dilemma: On my only hard drive, I have it partitioned for Windows 7 and Ubuntu 11, Earlier today I performed "Shrink Volume" on the Windows partition, successful, opened 22.74GiB I would like to increase my 10GiB Ubuntu 11 Partition to 16GiB, then create a partition for trying out chromium. 

  I know the following discussion I am going to sound like a noob but for simplicity bear with me. When I say "left" I actually mean tracks closest to the center of the cylinder and right, those further away.

  sda1 and sda2 are my Windows 7 Partitions, Then I have 22.75GiB of unallocated space from the shrink volume, then sda3 exteded, sda5 swap, and sda6 ext4 / 

  How do I "slide" the swap and Ubuntu 11 ext partitions to the left while maintaining their contents? 

  Or am I just as well backing up, then formatting the Ubuntu 11 partition? My first thought was to ghost the Ubuntu partition to the unallocated space then updating grub, but grub did not see it.

  I am extremely thankful for anyone that even bothered reading this far. Any help would be appreciated. I searched the forums but I didn't see any specifically pertaining to my quandry. If you know of one that would help a link to it would be great.

  The following is a screenshot of gparted's view of my HD

[IMG]http://i71.photobucket.com/albums/i130/Bodyholes123/gparted-Screenshot.jpg[/IMG]

---

### Post by Elfy on 2011-05-12
Boot with a livecd - either an OS one like ubuntu that has gparted or a partition editor. Right click on your swap partition - swap off - there should be no keys (mounted partitions) when you want to move things.

You'll need to resize the extended partition (sda3) before you can add the unallocated to sda6.

I suspect you'll need to move sda3 to the left so the unallocated space is all at the end. Then enlarge sda3 to the right. Refresh and the unallocated space should be inside the extended and you can add it to sda6.

---

### Post by Tanasqui on 2011-05-12
That worked, thanks.

---

