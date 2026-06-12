---
title: "Copy files from external linux disk onto XP"
date: 2010-01-07
forum: General Help
---

### Post by Gsyman on 2010-01-07
Hi

We have a hard disk from a defunct laptop from which we would like to recover some files (mainly .doc). The disk is running Ubuntu Linux and our PC is running XP Home, the disk is connected by SOHO usb Easy IDE cabling.
Every time we open the external hard drive we are prompted to format disk; is there a way to see the files to copy them? If not I guess we shall have to dualboot the PC with Ubuntu...

Thanks
Gsyman

---

### Post by clhsharky on 2010-01-07
HI Gsyman

Windows doesn't know any file system but its self! This fs driver
will let windows use Linux ext2 & ext3. Should do the trick.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Sharky

---

### Post by Gsyman on 2010-01-08
Thanks Sharky, instaled the program and can see the drive under E. Still asking me to format the drive, any ideas? Thanks, Gsyman.

---

### Post by oldfred on 2010-01-08
I would think just about any liveCD should let you boot from the CD and mount all the drives. Then you should be able to copy the data you want.

If the file system is damaged then use teskdisk which is on many recovery CD and can be downloaded from synaptic from the Ubuntu livecD.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by Gsyman on 2010-01-10
Hi
Used a Mepis live disk I had lying around, and was able to extract the files. Thanks for your help!

---

