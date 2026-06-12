---
title: "Accessing files across partitions"
date: 2010-03-04
forum: General Help
---

### Post by growthmetal on 2010-03-04
I have a partition with Windows Vista and another with Ubuntu 9.10.  What's the easiest way to set things up so that I can access the files in each partition while running the operating system in the other?

---

### Post by oldfred on 2010-03-04
I created a shared NTFS partition. Some windows only users even say you should have your windows data in a partition separate from the operating system.

Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by growthmetal on 2010-03-05
Thanks; what about accessing Linux files from my Windows partition?  (That's what I'm really worried about; I'm installing some drivers on Linux and I'd like to be able to recover my files from Windows if things go wrong.)

---

### Post by Daveski on 2010-03-05
> **growthmetal said:**
> (That's what I'm really worried about; I'm installing some drivers on Linux and I'd like to be able to recover my files from Windows if things go wrong.)

Trust me, a Linux LiveCD is WAAAY more useful at fixing things than Windows. If you want to change something on your Linux partition, boot to a recovery console, or directly to the Ubuntu LiveCD, mount your partition and manipulate your files.

The LiveCD is great because if you have a net connection you can 'install' new tools in the live environment and search the forums for help.

---

