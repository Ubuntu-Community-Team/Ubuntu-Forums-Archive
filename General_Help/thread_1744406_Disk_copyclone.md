---
title: "Disk copy/clone"
date: 2011-04-30
forum: General Help
---

### Post by bearcatrp on 2011-04-30
I have win7 and ubuntu on a 250gb hard drive. I would like to move this to a 1tb drive. Is it possible to clone the entire hard drive, including the MBR? Thought about doing a disk image but unsure if this is the answer. Any suggestions appreciated. Am using win7 64 pro and ubuntu 10.10..

---

### Post by Rubi1200 on 2011-04-30
Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by JRV on 2011-04-30
You can do it with the dd command or the Clonezilla disk.

Clonezilla is available here: [http://www.clonezilla.org/](http://www.clonezilla.org/)

The dd command is built in.

I have often heard the dd command referred to as "Destroy Data".
Read and understand the man pages before using it.  It can be dangerous.

---

### Post by Joe of loath on 2011-04-30
DD is less flexible than clonezilla for the purposes of disk backup and copying - for example, it doesn't expand partitions to fill a newer, larger drive.

---

