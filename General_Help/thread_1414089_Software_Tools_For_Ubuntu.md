---
title: "Software Tools For Ubuntu"
date: 2010-02-23
forum: General Help
---

### Post by newkid34 on 2010-02-23
Hey guys, Im new to ubuntu and i have a PC at home that i would like to use for testing hardware but i want to explore the capabilities of Ubuntu rather then install Windows on the machine.

Does anyone know of a piece of software that i can install on Ubuntu that would be able to 
Test the sectors and do a random read/write test to hard drives?

also what about an anti-virus that is compatible?

Any help is appreciated.

Thanks.

---

### Post by MooPi on 2010-02-23
Anti-virus isn't needed on an Linux machine. I have Clamav installed to check Windows partitions. As for a hard drive testing tool maybe, e2fsck. Another useful suite of applications is called ntfsprogs. This suite can test,fix, recover, resize ntfs file systems.

---

### Post by mkvnmtr on 2010-02-23
I believe what you want to check the disk is built in. Open a terminal and type man fsck and press enter. An explation of how to use the app will then come up. 
As for anti virus software there is no threat on a desktop system that justifies trying to run antivirus. If you need server aplication it will be much more productive if you learn to secure them. The threat to a linux is that you will install or allow to install malware. The threat does not come from a virus.

---

### Post by dehcbad25 on 2010-02-23
if you want to test the hardware and are new to Linux then use Knoppix liive CD. it has a ton of tools to test the hardware and it boots from a live CD, so there is no need to install OS.
btw, the post suggested using fsck, which does an excellent job with linux partitions, but for NTFS i still feel more confident with checkdsk. and you cannot run a check disk on a mounted partition, so running on / can only be done from the maintenance terminal, and that is why i like koppix. 
koppix also has tools to check memory, doing images partitioning and etc

---

### Post by newkid34 on 2010-02-23
thanks guys,

my next question is where can i find a 32-bit version of unbuntu server?

nevermind, i found out by clicking alternative options it was there.

---

### Post by whiskeylover on 2010-02-23
[http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)

---

