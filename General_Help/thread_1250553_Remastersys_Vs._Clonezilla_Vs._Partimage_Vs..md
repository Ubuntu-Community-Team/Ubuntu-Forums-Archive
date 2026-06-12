---
title: "Remastersys Vs. Clonezilla Vs. Partimage Vs. ???"
date: 2009-08-26
forum: General Help
---

### Post by C.A.G. on 2009-08-26
I'm Looking for the best way to clone/restore complete hardrives in either of these ways:

1) when hard disk fails you can just switch to another hard disk that contains the cloned image.

2) when hard disk fails you can insert an empty unpartitioned hard disk and boot up from DVD and clone hard disk image from that DVD to the new hard disk and then boot from the hard disk like nothing had happened.

A bunch of software has been mentioned in the forums such as remastersys, gparted, sysresccd, partimage, ghost, Mkcdrec, Clonezilla, etc. But which is the best?

Could you please state what you think the "best" software for accompishing either of these tasks is and why you believe it is the best (links would be great :)!)
Sorry about the long post.
Thanks in advance!

---

### Post by fragos on 2009-08-26
Your answer might help me. I wish to clone a partition onto a new disk and be able to boot from that partition. I know to change the UUID's in menu.lst and fstab on the new partition. I tried dd and it seemed to work but nothing was transfered and it left my new disk in a strange state until I used testdisk to clean things up. I had not mounted the receiving partition but got no error messages. I'm a little shaky on getting an MBR onto the new disk drive.

---

### Post by rbc on 2009-08-26
I use Clonezilla and love it for cloning. Why? Because it works great, was simple to use, so I have never needed to try anything else, although I hear partimage is just as good. This will answer #1 for you. Clonezilla can also accomplish #2 although I have never used it to make an image of a partition. It will create an image file which you can the “pipe” back to a pre-set up partition. I believe it also has the ability to break the file up into chunks to fit onto CDs or DVDs. I suggest getting partmagic. I has Clonezilla and many other useful tools, and is internet capable.

Fragos, unless I am misunderstanding your predicament, do you mean you were successful in using dd to clone a partition? I thought dd could only copy block devices?
sudo dd if=dev/sda of=path/to/file.txt bs=446 count=1 (will get you just the boot stuff)
sudo dd if=dev/sda of=path/to/file.txt bs=512 count=1 (will get you the boot stuff and the partition table). Then reverse the process to put the MBR on another hard drive
Using Gparted Live, and I assume partimage also, you can simply Copy/Paste a partition, and you mentioned you were proficient in amending the UUIDs afterward.

---

### Post by fragos on 2009-08-27
> **rbc said:**
> I use Clonezilla and love it for cloning. Why? Because it works great, was simple to use, so I have never needed to try anything else, although I hear partimage is just as good. This will answer #1 for you. Clonezilla can also accomplish #2 although I have never used it to make an image of a partition. It will create an image file which you can the “pipe” back to a pre-set up partition. I believe it also has the ability to break the file up into chunks to fit onto CDs or DVDs. I suggest getting partmagic. I has Clonezilla and many other useful tools, and is internet capable.

Fragos, unless I am misunderstanding your predicament, do you mean you were successful in using dd to clone a partition? I thought dd could only copy block devices?
sudo dd if=dev/sda of=path/to/file.txt bs=446 count=1 (will get you just the boot stuff)
sudo dd if=dev/sda of=path/to/file.txt bs=512 count=1 (will get you the boot stuff and the partition table). Then reverse the process to put the MBR on another hard drive
Using Gparted Live, and I assume partimage also, you can simply Copy/Paste a partition, and you mentioned you were proficient in amending the UUIDs afterward.

The command I used, right or wrong was "sudo dd if=/dev/sdb5 of=/dev/sda2. Thanks for the info.

---

### Post by C.A.G. on 2009-08-27
Thanks rbc, I'll try Clonezilla again.  The  last time I tried it I got several errors and could not figure it out.  But I just found a post that pointed me to a "tutorial" for the software.  Going to try it now...

Thanks:)

---

