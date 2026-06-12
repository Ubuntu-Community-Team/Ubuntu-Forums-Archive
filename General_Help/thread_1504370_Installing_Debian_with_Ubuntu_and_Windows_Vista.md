---
title: "Installing Debian with Ubuntu and Windows Vista"
date: 2010-06-07
forum: General Help
---

### Post by Axolotl9250 on 2010-06-07
I have a large Ubuntu partition and a smaller Windows Vista partition in-case I should ever need to for compatibility at uni. Anyway I want to make the Ubuntu partition smaller and put Debian on and have a crack at it. Trouble is, the partition manager in windows won't touch the linux partition and I can't resize it from in ubuntu as it won't let me unmount it (I assume because it's using it for the Ubuntu I'm currently using so it's occupied). I've had a look at parted and resize2fs (although I can't figure out how to use that because all the commands are unexplained in the terminal). So I can't figure out how to clear some space and all the tutorials on partitioning say "oh unmount it" which it all very well and good if it will let you, but I can't. I had a look at the partitioner in the installer for Debian but it gave me some error messages about the kernel being uninformed or the change until a reboot so I decided to leave it and write here. If anybody could give me some advice I would be very grateful.

Cheers.

---

### Post by Smart Viking on 2010-06-07
The best way would be to burn a live CD with Ubuntu or a distro of your choice, then boot from it and resize from the live CD.

I think the ubuntu live CD have gparted, use that. :)

---

### Post by Axolotl9250 on 2010-06-07
I've loaded up the live CD and started GParted, I've clicked on Swapoff on my /dev/sda6 linux swap partition (both it and the main bit (/dev/sda5) are part of an extended partition (/dev/sda2) that makes up the whole ubuntu install as done by the automated install and guided partition in the first place when installing next to windows). I did this as otherwise when it try to right click move/resise the extended partition the option is faded out. I bring up the resise box with a drag bar and some boxes to type space before and after partition, and the new size, but when I try to alter them they just reset to what they were before as soon as I remove the cursor, the resize bar thing will also not drag. It tells me the min size is 151960 MiB and the max size is identical.

---

### Post by oldfred on 2010-06-08
When partitions are inside a extended partition you have to shrink the logical first then shrink the extended. If expanding you have to expand the external then you have space to expand the logical. the container has to be adjusted as well as the contents of the container. 
You may have to do it in two steps.

---

### Post by Axolotl9250 on 2010-06-08
I've just tried it now. Unfortunately no dice. When I tried to resize the logical ext4 partition it give me just 1MiB of resize/wiggle room and even if I try that it gives me an error. An Icon appeared next to it which was like a orange warning "!" and so I used the Right-Click->Check operation on the disk and a second into it it came back with the same error:

e2fsck -f -y -v /dev/sda5
The superblock could not be read or does not provide a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem and not swap or ufs or something else, then the superblock is corrupted and you might try running e2fsck with an alternate superblock : ef2sck 8193 <device>.

This is puzzeling as the partition is formatted at ext4, not ext2 as it says? Little unsure of how to proceed now - is it safe/wise to reformat as ext2? It seems that's what GParted is looking for, although the whole auto install thing from live CD the first time obviously set up ext4 and not ext 2.

[EDIT] Just tried to reformat as ext2, It still didn't work AND the Grub is now screwed up. Looks like time for a reinstall. It has a vista loader on it if that makes any difference.

---

### Post by oldfred on 2010-06-08
ext4 & ext3 are just versions of ext2 with journaling and maybe a few other improvements but still the same basic file structure. the journal is what would allow you to recover data. Converting to ext2 may have deleted all the recovery capability.

---

### Post by Axolotl9250 on 2010-06-08
O.K. I'll remember that next time. I did a resize of the partition from the Debian installer CD and it all worked apart from the loader that comes up at the beginning only listed Debian and the Windows 7 Loader. If I were a bit more patient I'd try and figure that bit out and get the Ubuntu partition included on that menu, but as I need the laptop I'm using for a Biology Field Trip to Ireland I need it running quickly. So I've backed up my work and Re installing everything but this time putting on Windows on and splitting the hard-rive, putting on Debian, and then Ubuntu so the live CD for Ubuntu can eliminate the complication of resizing and boot menu's. If I run into any complication I'll return.

---

### Post by Axolotl9250 on 2010-06-08
Got it all working now :) Cheers.

---

