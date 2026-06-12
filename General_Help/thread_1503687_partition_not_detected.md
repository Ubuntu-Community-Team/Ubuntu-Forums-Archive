---
title: "partition not detected"
date: 2010-06-07
forum: General Help
---

### Post by viscorus2004 on 2010-06-07
I've ubuntu 9.10 installed, there are 5 partitions inside but when I check in partition manager application such gparted it does not appear, I mean it show "unallocated" very weird ...

I run terminal and type fdisk -l but nothing happen

anybody know how to solve this?? 

sorry for my bad english..

---

### Post by john newbuntu on 2010-06-07
Please open up a terminal, run the following command and paste the output:
```
sudo fdisk -l
```
You could also try posting a screenshot of gparted main screen showing the drive that you are interested in.

---

### Post by viscorus2004 on 2010-06-07
> **john newbuntu said:**
> Please open up a terminal, run the following command and paste the output:
```
sudo fdisk -l
```You could also try posting a screenshot of gparted main screen showing the drive that you are interested in.

ok fdisk is works but still not work for partition manager :(
sorry I dont know how to make spoiler, I just press Print Screen key on keyboard and upload to imageshack, maybe its too big

here the image link :[U]
[ image here ]("http://img10.imageshack.us/i/screenshotvy.png/")
[/U]

---

### Post by Mark Phelps on 2010-06-07
> **viscorus2004 said:**
> ok fdisk is works ...

You were asked to post the output of the the "sudo fdisk -lu" command.  

Until you do that, there's little we can do to help you solve the problem. We're not mind readers here!

---

### Post by john newbuntu on 2010-06-07
The fdisk output is not fully visible in the image that you have posted.  However, there appears to be an overlap between two of the primary partitions /dev/sda3 and /dev/sda4, which could probably be why gparted is getting confused.

I have not encountered this problem but have seen others who have had a similar issue solve it using testdisk.  But please back up any possible data you can from your disk prior to running testdisk.  Here is a link that might help you: 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You might also want to wait and get some input from someone who has done this before.

---

