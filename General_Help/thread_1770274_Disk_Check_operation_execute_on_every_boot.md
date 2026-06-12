---
title: "Disk Check operation execute on every boot"
date: 2011-05-29
forum: General Help
---

### Post by Milan Mendpara on 2011-05-29
:) hi ...... !

i'm using ubuntu 10.10 .... i'm very pleased with its performance except one small disturbance 

at every boot ubnutu** DiskChecking operation** is performed ...... if i cancel this operation then it won't allow me to go ahead or sometime **file system won't be mount** perfectly. ........ 

i think u r the best person to solve this small problem .,......... 

tanks in advance ....... :))

---

### Post by katykat on 2011-05-29
[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

Much depends on how you aborted the operation. 

If you forced an abort, such as by rebooting, there may be corruption to the file system. 
Its normal to run a basic check at startup, but normally it should take more than a few seconds. 

If the problem persists boot to a Linux bootCD (should be the install CD, and choose 'Live') and do an fsck sda1 (if on drive C: or the first HD and partition...) and let it complete its operation, no matter how long it takes. 

If the problem still persists remove the errors=remount-ro attribute (if there is one) in /etc/mtab  and /etc/fstab (after backing it up) and seeing if it works if replaced with errors=remount.  

However there is a possibility of hard drive problems in the making, so it would be well advised to back up all valuable  data as soon as you can acess the drive. 

Google on the use of SMART utilities for Linux to test the drive itself (rather than the filesystem).

---

