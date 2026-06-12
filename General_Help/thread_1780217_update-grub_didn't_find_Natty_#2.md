---
title: "update-grub didn't find Natty #2?"
date: 2011-06-11
forum: General Help
---

### Post by MrRichard on 2011-06-11
Here's the short story:
I have Natty, Natty installation #2 and Windows 7 on my one hard drive. Grub can only see one Ubuntu installation (Natty #2) and Windows 7 after trying the update-grub command. Is there any way I can either:
[LIST]
[*]Update/install Grub so Natty is visible, or
[*]Boot into Natty in any possible way
[/LIST]

Long story:
Hi there, I wanted to try out Linux Mint Debian (LMDE) and followed a tutorial on how to dual boot it and Natty. Before I knew it, Windows 7 was the only option in Grub to boot from. The partitions of all 3 OSes are there, but only Windows can be seen by Grub.

So, I deleted LMDE's partition and left Ubuntu and Windows 7 alone while I tried various other tutorials on how to fix Grub. No luck so far.

Now I decided to install a second Ubuntu OS to fix the issue, but that didn't work.

---

### Post by drs305 on 2011-06-11
Please boot into Natty and then download, extract, and run the boot info script. This will produce a file called RESULTS.txt 

RESULTS.txt will give us a good look at your boot files and Grub2. Click on the "BIS" link in my signature line to take you to the download site.


**Added:**
If you know the Natty partition, at the G2 menu highlight Natty2 and press 'e'. You can remove the search line, change the UUID in the linux line to "root=/dev/sd**XY**" and, if the kernel is the same, press CTRL-x to boot.

But run the BIS from Natty #2 if you can't, or try "sudo update-grub" if you get into Natty 1.

---

### Post by rostom_zer on 2011-06-11
not so hard !!!

> sudo fdisk -l lets say tat your partition where ubuntu is installed is sda1 ) if not then change it into yours !

> sudo mount /dev/sda1 /mnt> sudo mount /dev/sda1 /mnt/boot> sudo mount --bind /dev /mnt/dev/> sudo chroot /mnt> grub-install /dev/sda> sudo umount /mnt/dev> sudo umount /mnt> sudo rebootdone...

---

