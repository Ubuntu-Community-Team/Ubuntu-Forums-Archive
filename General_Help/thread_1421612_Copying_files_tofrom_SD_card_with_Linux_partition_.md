---
title: "Copying files to/from SD card with Linux partition and Windows PC"
date: 2010-03-04
forum: General Help
---

### Post by gglaser on 2010-03-04
Hi, I have an SD card that I formatted using my Ubuntu machine to contain one raw Linux partition and one FAT32 partition. Does anyone know of a way to be able to copy files to/from the SD card and my Windows PC? Right now, when I plug the SD card into my Windows PC, the FAT32 partition doesn't appear. When I try to copy files from my Windows PC to the raw Linux partition on the SD ard, I get "bad magic number" errors on the device that I use the SD card with. Is there some utility I can use on my Windows PC to be able to correctly read this SD card? It would be very convenient to have that for travel, etc when I don't have easy access to the Ubuntu machine. Any suggestions would be appreciated - thank you!!

---

### Post by Mark Phelps on 2010-03-04
Don't know what a "Raw Linux partition" is.  Know about Ext2, Ext3, Ext4 filesystems.  So, if it's one of those, you need to tell us.

As to the FAT32 partition, don't know why it doesn't get seen, but for future purposes, you would better using an NTFS partition to share data between Linux boxes and Windows boxes.

---

