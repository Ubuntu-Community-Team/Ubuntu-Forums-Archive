---
title: "Problems Dual Booting windows 7 and ubuntu"
date: 2011-07-10
forum: General Help
---

### Post by Garykirk on 2011-07-10
hello
i tried to dual boot windows 7 and ubuntu and ran into some problams. i am new to Linux and have installed ubuntu on a new partition and i decided to uninstall it and try another distro of Linux so i booted into Mandriva install and deleted the partition of ubuntu (not reliseing that i will kill my GRUB launcher) i then used my windows 7 install disk to fix the MBR and now i have two partitions that won't delete within windows and ubuntu doesn't recognize them.
[IMG]http://img850.imageshack.us/img850/5779/snap2011071018h33m42s00.png[/IMG]
is there any way of deleting these partions without formatting and reinstalling windows and ubuntu?
thanks
GaryKirk :)

---

### Post by idoitprone on 2011-07-10
live cd then gparted?    or use fdisk on the harddrive   or use gdisk or sgdisk or parted if it is a gpt partition table?  ubuntu should recongnize all you partitions

---

### Post by Garykirk on 2011-07-10
Thanks :)

---

### Post by Bucky Ball on 2011-07-10
Welcome.

Windows won't delete an EXT partition. Doesn't know what they are.

Boot from a LiveCD and use Gparted (as suggested) to delete them (or boot to a Linux desktop and use the partition manager there to do the job).

Incidentally, the partition in green at the end is not actually a partition; it's free space so you are only looking at killing the third partition (Healthy). But making free space by deleting the third partition and adding it to the free space you already have is still probably not enough space to install Ubuntu anyhow. Where you going to put it? You would need to shrink C: (in Windows) but defrag it a number of times before you do that.

The other issue is that you already have three primary partitions. The limit is four, Linux (theoretically) needs at least two (/ and /swap), therefore you need to create an extended partition (which is seen as the fourth primary partition) and put your Linux partitions inside that (on logical partitions).

Hope that all makes sense. ;)

* Forget using Windows if you want to manipulate, create, resize, delete Linux partitions (EXT*).

---

