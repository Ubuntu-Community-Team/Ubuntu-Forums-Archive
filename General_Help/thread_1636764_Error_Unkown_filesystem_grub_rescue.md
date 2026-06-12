---
title: "Error Unkown filesystem grub rescue?"
date: 2010-12-03
forum: General Help
---

### Post by Noaptus on 2010-12-03
Hi.

My sister got a Dell laptop installed Ubuntu 9.10

Her 3 year old son got to the laptop and i have no idea how hey did this.

He accidentally deleted the hole hard drive + file system ext4.

Can com one tel me how the blip i can recover the lost data.

Now if i do this sudo fdisk -lu i get this

Device boot            Start      END       Blocks     ID      System
/dev/sda1     *       19131      19458     2620416     C     w95 FAT32 (LBA)
/dev/sda2             18707      19457     6032407+    5     Extended
/dev/sda5             18707      19457     6032376     82    Linux swap / Solaris


And when i do this sudo sfdisk -d i get.

# partion table of /dev/sda
unit: sectors

/dev/sda1 : start=307337216,  size=  5240832,  Id= C,  bootable
/dev/sda2 : start=300511890,  size= 12064815,  Id= 5
/dev/sda3 : start=        0,  size=        0,  Id= 0
/dev/sda4 : start=        0,  size=        0,  Id= 0
/dev/sda5 : start=300511953,  size= 12064752   Id= 0

And when i use gparted i get the hard disk is unallocated.


Can some one help me please :)

---

### Post by sikander3786 on 2010-12-03
It is not possible to delete the Ubuntu Root Partition from inside Ubuntu as you need to unmount the partition to either format/resize/delete it. And that needs to be done from a Live CD or some other OS :confused:

These links will be helpful to start with.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Noaptus on 2010-12-03
Hi.

Thank you fore the quick replay.

Okay i try to use DataRecovery 

sudo swapoff -a

sudo parted /dev/sda

rescue ( START END ) i have no idea what to use 
i did try to use this rescue 18707 19457 and the error i got is

Error: Can´t have overlapping partitions

---

### Post by sikander3786 on 2010-12-03
Try the Testdisk section. It is simpler and easier I feel.

---

### Post by Noaptus on 2010-12-05
Hi.

Thank you for the answer. I downloaded the [partedmagic]("http://partedmagic.com") and use the TestDisk and i did get my files back :)

---

### Post by sikander3786 on 2010-12-05
You are Welcome :-)

More than that, glad to know that you were able to recover your data ;-)

---

