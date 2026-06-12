---
title: "GPARTED will not play with me."
date: 2006-04-22
forum: General Help
---

### Post by Mookawaka on 2006-04-22
I am attempting to micro-manage my partitions on a laptop with a small hard drive (20 GB).
Unfortunately Windoze(TM) cannot be banished as of yet, as Lexmark will not play nice with open source in regards to printer drivers. :( 
I would like to shrink the NTFS partition that I have, and use the space to increase my shared FAT32 partition that is right next to it.
I have proceeded by:
1) Defragmenting the NTFS partition.
2) Booting Ubuntu
3) Unmounting appropriate drives from the command line.
4) Running GPARTED
5) Resizing NTFS to desired size and clicking "APPLY"

At this point I am presented with the error:
"At least one operation was applied to a busy device.
A busy device is a device with at least one mounted partition.
Because making changes to a busy device may confuse the kernel, you are advised to reboot your computer."

I am convinced (in a naive new user way) that I have successfully unmounted the drives before proceeding, as they no longer appear and GPARTED also shows them as unmounted.

Could anyone clear this up for me?

---

### Post by zaba on 2006-04-22
Have you tried running GPARTED from a "Live CD" or from anywhere besides the hard drive in the laptop? It might not want to run since at least one of the partitions of the hard drive is loaded.

---

### Post by PriceChild on 2006-04-22
Do you have a swap partition on your drive? as the live cd will probs load it.

---

### Post by Herman on 2006-04-22
> I am convinced (in a naive new user way) that I have successfully unmounted the drives before proceeding, as they no longer appear and GPARTED also shows them as unmounted.  I think I used to use the command 'swapoff' to unmount the swap area, in addition to unmounting the partititions, when I used to use GParted from my Ubuntu installs. That was a long time ago, before the GParted Livecds were available.
I agree with zaba, you should use the latest GParted Livecd.  My right-hand sig link will lead you to where you can download the .iso for one. It's only a small download and contains the most up to date, cutting edge software. It will work much better than the OS-installable GParted version. You don't have to bother unmounting anything when you use GParted Livecd either, it has a trick of mounitng everything as 'fake-raid' or something like that automatically for you. It's extremely simple to use. 
Regards, Herman :D

---

### Post by Mookawaka on 2006-04-23
The GPARTED live disk worked like a magic charm.  Thank you to everyone for the assistance.

---

