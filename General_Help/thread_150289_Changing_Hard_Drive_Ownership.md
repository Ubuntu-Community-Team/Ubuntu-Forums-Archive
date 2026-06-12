---
title: "Changing Hard Drive Ownership"
date: 2006-03-25
forum: General Help
---

### Post by Linkhiei on 2006-03-25
Hello Im trying to partition my ubuntu hard drive (hda1) with a FAT32 partition so that I can have it read by ubuntu and Windows. But when I try to partition it, it says Im not the owner. I try #sudo chown username /dev/hda1 but it still doesnt say im the owner when i look at the drive properties. Does anyone know how to change myself to the owner?

---

### Post by morguns on 2006-03-25
what about using a gparted live cd?

---

### Post by StefanoCole on 2006-03-27
Did you try rebooting your system? Did the ownership change?

Stefano

---

### Post by akiro.yamamoto on 2006-03-27
If the hard drive has only 2 partitions:
hda1 mounted as /
hda2 <SWAP> you will be unable to re-partition / re-size the partition as the partitions have to be unmounted.
Your best bet in a situation like this is to use the gparted live cd or use a rescue
CD like [** THIS !!! **](http://www.sysresccd.org/Main_Page) to repartition your hard drive....
Hope this info helps ;)

---

