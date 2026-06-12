---
title: "unable to boot /home is not ready"
date: 2011-08-20
forum: General Help
---

### Post by terryrusso on 2011-08-20
after my recent update in ubuntu 11.04 64bit that installed a new kernel, my first boot into the os stalled for a long while. i think it said it was checking the disk but did not show any signs that it is working. i left it for half an hour or so and had to force restart it.

from then on, my ubuntu gives a black screen when i boot. choosing recovery mode it tells me it cannot find /home saying /home is either not ready or not there. 

i tried to do a fsck and it says fsck.ext4 Unable to resolve UUID=e8629....not impt. probably the /home partition that is messed up. i used gparted to look at my partition and true enough my /home partition is now an unallocated partition space.

this is my setup. i have a win 7 ubuntu dual boot
Device   Boot Start End  Blocks    Id System
/dev/sda1        1  1913 15360000  27 Unknown
/dev/sda2 *    1913 1926 102400     7 HPFS/NTFS
/dev/sda3      1926 71017 554980469 7 HPFS/NTFS
/dev/sda4     71018 77826 54686721  5 Extended
Partition 4 does not start on physical sector boundary
/dev/sda5     75394 7782619530752  83 Linux

I thought I could save myself the trouble and just install over the current ubuntu install but I'm having trouble booting from the cd. 
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/754130](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/754130)
this describes my problem with booting from ubuntu live cd pretty well. so I am at wits end on how to get my ubuntu working again.

I have a i7-2630QM processor Acer Aspire 4750G laptop.
Thanks in advance to any kind souls willing to help.

---

### Post by allwimb on 2011-08-20
try to boot on a livecd and check if your /home parition exists or not and check if the fstab find it really or not.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by terryrusso on 2011-08-20
hi, thanks for your time. livecd does not boot was the second problem i have. in my previous post i posted a link describing my problem with livecd. so basically im quite screwed. can't boot ubuntu and can't boot ubuntu 11.04 livecd either. perhaps i can try a older version of ubuntu livecd. i tried booting linux mint 9.0's livecd and i din have any problem.

---

### Post by terryrusso on 2011-08-20
it's confirmed. /home is empty when i mount /dev/sda5. So is there a way to fix my partition?

---

