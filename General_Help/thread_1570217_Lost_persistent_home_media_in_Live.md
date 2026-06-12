---
title: "Lost persistent home media in Live"
date: 2010-09-07
forum: General Help
---

### Post by basicbill on 2010-09-07
I partitioned a 32 gB flash drive to one 8 gig and one 24 gig partition. Both fat32. I wanted to be able to access the 24 gig partition from XP.
I installed a persistent 10.04 on the 8 gig partition.
All ran well for about 3 weeks. 

Today during boot up I noticed that it had stalled at "creating live session user". I left it there for several minutes and then powered down to retry.
Several attempts to boot left me at the same spot.

I looked at the boot up messages and noticed this error... "unable to find persistent home media".

I don't have a ton of save info on the live user account but I would like to be able to fix this type of problem.

Has anyone seen this error message before? Any idea on how to recover the persistent live user?

tia

---

### Post by bodhi.zazen on 2010-09-07
Try accessing the data from a live CD or Windows.

If that fails you can try testdisk.

---

### Post by basicbill on 2010-09-07
testdisk? I am running from a backup 10.04 persistent.
I tried to install testdisk .... this is what I got.

[I]ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk[/I]

I have regular and universe sources configured.

---

### Post by bodhi.zazen on 2010-09-07
> **basicbill said:**
> testdisk? I am running from a backup 10.04 persistent.
I tried to install testdisk .... this is what I got.

[I]ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk[/I]

I have regular and universe sources configured.

Try ```
sudo apt-get update
sudo apt-get install testdisk
```

It is in the repos

[http://packages.ubuntu.com/search?keywords=testdisk](http://packages.ubuntu.com/search?keywords=testdisk)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/](http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/)

---

