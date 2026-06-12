---
title: "Software RAID Setup"
date: 2010-03-26
forum: General Help
---

### Post by jwhitt on 2010-03-26
Hello, 

sorry if this post is in the wrong location. i am attempting to setup a software raid 5 solution. I have 6 1TB drives all works fine except when i attempt to format the array i get a Warning: The partition is misaligned by 48128 bytes. This may result in very poor performance. repartitioning is suggested. Any thoughts as to what i am doing wrong?

I ensured that the drives had no partition tables on them added them to the array, then went to format volume and i get that warning.

---

### Post by tyebud on 2010-04-28
I'm also experiencing this.

---

### Post by lyall on 2010-04-28
in the Community Documentation InstallationSoftwareRAID
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

in the Community Documentation Documentation Search for Raid
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

in the Community Documentation [https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")
do a search for **Raid**

the above info should help you set up your raid system

good luck and have fun learning

---

### Post by tyebud on 2010-04-29
Thank you for pointing out those resources.

Just a little background for the next guy that has a problem like mine.

I was not setting up my array during installation.  I already had Ubuntu set up on a single disk and was using the disk utility to create additional volumes.

With that said, it was a silly oversight.

You need to create a partition table on your disks before you create the array in order to avoid the misalignment error!  Disk utility didn't warn against this which left me hunting for more info.

So there you go:

If you are building a raid array in Disk Utility, make sure to create partition tables on your disks before creating the array!

---

