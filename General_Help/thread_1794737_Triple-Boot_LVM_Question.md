---
title: "Triple-Boot LVM Question"
date: 2011-07-01
forum: General Help
---

### Post by hello cruel world on 2011-07-01
I am setting up a triple-boot machine, with an encrypted partition of Ubuntu. The machine is using Windows 7, Ubuntu 11.04, and BackTrax 5. Would the following be the right partition scheme?

Windows7 Recovery
Windows7 Main
Ubuntu Boot(Unencrypted ext4)
Ubuntu Swap (Encrypted LVM)
Ubuntu Main (Encrypted LVM ext4)
BackTrax Swap 
BackTrax Main (ext4)
Storage (NTFS) 

If so, what is the proper order of operation for establishing the LVM encryption? I attempted it last night, and was left with no root partition, so I think I didn't follow the logical order of creating the Ubuntu LVM partitions.

---

### Post by dino99 on 2011-07-01
no /home partition ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by hello cruel world on 2011-07-02
The storage partition is meant for ubuntu and w7 to use it, which is why I left it NTFS.

---

