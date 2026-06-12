---
title: "Asus 1005HA, how many partitions on HD"
date: 2009-08-08
forum: General Help
---

### Post by Kansasguy on 2009-08-08
Does anyone know how many partitions are there on the hard drive of a 1005ha out of the box.  C:   D: and what else?

The reason I ask is that I loaded linux Mint, and then took it off, and didn't know exactly what partitions were the original.   One of them is a FAT .   Any thoughts?

(also, any thoughts on whether Mint -a version of Ubuntu Jaunty- should be dual booted "within Windows" or "not within Windows"?)

---

### Post by michy99 on 2009-08-08
To see the partitions on your disks:```
sudo fdisk -l
```I would go with the normal 'outside of windows' set-up. It doesn't make any sense to me to make your linux system dependent on Windows in any way.

---

### Post by Kansasguy on 2009-08-08
It seems from the following post that the 4 partitions on my new machine (Asus eee 1005ha) are all supposed to be there.  This machine is a netbook and has no cd drive, so I am learning about mounting things (like OS's) from a flash drive.  

Can you advise the difference between mounting "in Windows" and out?

Thanks again for your reply


[http://forum.eeeuser.com/viewtopic.php?id=779](http://forum.eeeuser.com/viewtopic.php?id=779)

---

### Post by michy99 on 2009-08-08
If you are running the OS from a flash drive, and not installing it to an internal harddrive, then it doesn't apply. I was referring to the Wubi install which install Ubuntu in a file on the Windows partition instead of on a separate partition.

---

### Post by Kansasguy on 2009-08-08
I installed Mint "in windows", with a flash drive using VCD (I think), but had problems with some things and ended up formatting the D: drive to get rid of it to start over. Will install it again "in windows" unless I can find out how to do it outside of Windows. Remember, this thing has no CD drive so everything has to be done with a flash drive.  Again, any help greatly appreciated.    ht

---

