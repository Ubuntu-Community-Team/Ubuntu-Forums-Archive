---
title: "Get rid of ubuntu and partitions"
date: 2009-08-08
forum: General Help
---

### Post by mk12 on 2009-08-08
I installed ubuntu on my macbook and made partition for it but its not really working and I don't want it anymore please how can I make it all one partition with just macintosh hd? Macintosh hd is still on my computer, and I also have a complete bootable backup of it on my external hard drive. Please how can I get it back to normal! Thanks.

---

### Post by azmo35 on 2009-08-08
Hi,i never have a Apple so maybe this is a litle gest but with a live cd use the partition editor delete Ubuntu Partitions,and them resize. Or delete all partitions and make a fresh install of your backup,again this is a gest,i hope this can help you some how.

---

### Post by mk12 on 2009-08-08
I tried using the cd to boot ubuntu but its not working anymore. How can I remove the drive? There's still a "Linux swap" partition that won't get deleted, I think that's whats not letting me resize the Macintosh hd ( I get error: MediaKit reports no such partition when i try to resize).. Please someone help!

---

### Post by lisati on 2009-08-08
There's still a "Linux swap" partition that won't get deleted,[/QUOTE]
You'll need to turn off swapping before trying to delete the swap partition. Right-click on the swap partition, click on "swapoff", and you should be able to delete it.

---

### Post by mk12 on 2009-08-08
I'm in os x not ubuntu, ubuntu isn't even working.. will an archive and install fix this?

---

### Post by CTBuckweed on 2009-08-08
> **mk12 said:**
> I installed ubuntu on my macbook and made partition for it but its not really working and I don't want it anymore please how can I make it all one partition with just macintosh hd? Macintosh hd is still on my computer, and I also have a complete bootable backup of it on my external hard drive. Please how can I get it back to normal! Thanks.
Well, I'm am (or used to be) an old Windows guy. Does OS-X have some type of partition manager where you can just delete and manage partitions? At home, I uas Partition Manager, a DOS/floppy tool that let's me manage (create-delete-resize partitions). First, make sure that you can boot directly into the Mac OS without using Grub (the linux boot loader). Grub usually exists on the linux partition.

You may have to boot from the MAC install CD and reload the Mac boot loader on the boot sector, etc.

Again, I know nothing about Macs, so I can't really help with the details.

Sorry you don't like Ubuntu. I like it a lot. I hardly ever boot into Windows anymore.

---

### Post by mk12 on 2009-08-09
Incase anyone had the same problem, I used Gparted live cd to remove the linux swap partition. When I tried booting, I got broken folder icon (crossed circle) but I removed battery and held power for 5 seconds and it booted, then I tried resizing macintosh hd to take up all the space (in disk utility), but it didn't work, so then I "repair disk permissions" and resized again and it worked.

---

### Post by Post Monkeh on 2009-08-09
> **mk12 said:**
> Incase anyone had the same problem, I used Gparted live cd to remove the linux swap partition. When I tried booting, I got broken folder icon (crossed circle) but I removed battery and held power for 5 seconds and it booted, then I tried resizing macintosh hd to take up all the space (in disk utility), but it didn't work, so then I "repair disk permissions" and resized again and it worked.

glad you got sorted.  you should have been able to do everything from a livecd using gparted (you should have been able to just delete the ubuntu partitions, turn off swap on the swap partitions and delete them, then rezize the osx partition)
out of interest, what kind of processor is in your macbook and what version of ubuntu (ie x32, x64, powerpc) were you installing?

---

### Post by mk12 on 2009-08-10
Macbook5,2/Intel Core 2 Duo Processor 2.13 GHz/2GB RAM. Was installing ubuntu desktop amd64 9.04. What do you mean do everything in gparted? First I deleted all the partitions in disk  utility in os x (exceot linux swap because It couldn't delete it), so then I used gparted livecd to Delete it (not turn swapping off, whatever that does), then all there was left was macintosh hd, so in disk utility on os x I did a repair disk permissions on the internal hd, then resized macintosh hd to take up the whole thing. And now it restarts fine, everything back to normal, no more broken folder icon when starting up.

---

### Post by Post Monkeh on 2009-08-10
> **mk12 said:**
> Macbook5,2/Intel Core 2 Duo Processor 2.13 GHz/2GB RAM. Was installing ubuntu desktop amd64 9.04. What do you mean do everything in gparted? First I deleted all the partitions in disk  utility in os x (exceot linux swap because It couldn't delete it), so then I used gparted livecd to Delete it (not turn swapping off, whatever that does), then all there was left was macintosh hd, so in disk utility on os x I did a repair disk permissions on the internal hd, then resized macintosh hd to take up the whole thing. And now it restarts fine, everything back to normal, no more broken folder icon when starting up.

i just meant you could have done it all in gparted (deleted the ubuntu/swap partitions and extended the osx partition into the new space), but at least you got sorted

---

