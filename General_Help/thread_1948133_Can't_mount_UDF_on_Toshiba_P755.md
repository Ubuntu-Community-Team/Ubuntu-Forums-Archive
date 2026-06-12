---
title: "Can't mount UDF on Toshiba P755"
date: 2012-03-27
forum: General Help
---

### Post by ChrisNelson1022 on 2012-03-27
I recently bought a Toshiba Satellite P755 laptop.  It came with Windows 7 Professional 64-bit pre-installed which I wanted to preserve for those things you just have to do in Windows.  I made two complete sets of System Repair and System Image DVDs and the creation process supposedly verified them.  Now I have Ubuntu 11.10 installed and VirtualBox installed.  I created a VM for W7, copied the BIOS settings into the VM, and got the System Repair DVD to boot and prompt me for my System Image (it says to insert the last volume of the multi-volume image).  I swap DVDs and ... nothing.  

I Googled around and found something about a UDF driver which I installed (sorry, I don't remember what it was) but that didn't help.  I have two sets of three System Image DVDs.  All six appear free from major defects.  Most appear perfect, one or two have tiny, tiny scratches, one has a little finger print in the middle.  When I insert any of them and try to mount, the disk spins briefly then gives up.  `dmesg` reports something like:

```
[ 4962.539260] udf: udf_read_inode(ino 75647) failed !bh
[ 4962.576922] udf: udf_read_inode(ino 75646) failed !bh
[ 4962.614545] udf: udf_read_inode(ino 75645) failed !bh
[ 4962.652164] udf: udf_read_inode(ino 75644) failed !bh
[ 4962.773150] attempt to access beyond end of device
[ 4962.773160] sr0: rw=0, want=6915428, limit=302592
[ 4962.773165] udf: udf_read_inode(ino 1728856) failed !bh
[ 4962.773177] attempt to access beyond end of device
[ 4962.773182] sr0: rw=0, want=6915424, limit=302592
[ 4962.773185] udf: udf_read_inode(ino 1728855) failed !bh
[ 4962.773191] attempt to access beyond end of device
```

It defies belief that all six of my DVDs are damaged and unreadable in the drive that made them.  Since I've never read a UDF disk on this computer from Linux I suspect a missing driver or something but several evenings searching the web hasn't found any solution.  Lots of clues about mounting UDF images but nothing about mounting disks.  Any thoughts?

Thanks!

---

