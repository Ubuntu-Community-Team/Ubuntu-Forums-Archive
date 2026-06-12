---
title: "Ubuntu does not boot after install."
date: 2009-10-22
forum: General Help
---

### Post by kilinu5889 on 2009-10-22
Ok, I have tried installing Ubuntu 9.04 multiple times. After every attempt I have had no luck. It would either crash after getting to the disk partitioner. Or it would fully install, then it would not boot after the install was completed.I do not know what to do. I have burned multiple CD's of Ubuntu.I wrote them all at either 4x or 8x nothing higher. My friend's dad has had the same problem with his PC. His specs are almost similar to mine. Except the video card,the motherboard, and he has 1GB of RAM. I'm starting to think it is an HDD problem. What should I do? My system specs are as follows.

 	
 	
Intel(R) Pentium(R) 4 CPU 3.00GHz (2 CPUs), ~3.0GHz	
2048MB RAM	
250 GB SATA
Video Card: 	
NVIDIA GeForce 9400 GT	
Windows 7 Ultimate RC 32-bit
UltimSpeakers (SigmaTel High Definition Audio CODEC)		
D945GCL

---

### Post by fluffman86 on 2009-10-22
use [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) to verify the md5sum of the file you downloaded, and run the "check CD for defects" option when booting from the CD.

If that all tests OK, then maybe Ubuntu is having trouble partitioning your hard drive.  Try manually partitioning with [http://gparted.sf.net](http://gparted.sf.net) and installing Ubuntu then.

---

### Post by kilinu5889 on 2009-10-22
Ok, will do.

---

