---
title: "wiping a hard drive with a mounted partition"
date: 2010-12-22
forum: General Help
---

### Post by jsvidyad on 2010-12-22
Hello,

  What happens when you wipe a hard drive which has a partition that is mounted? I was using ubuntu 9.10 live CD but I had one partition on a hard drive mounted. Then, I started to wipe the entire hard drive with random characters using dd. Only later I realized that I hadn't unmounted that partition. what could have happened? Could the Live CD have been damaged?

---

### Post by garvinrick4 on 2010-12-22
> **jsvidyad said:**
> Hello,

  What happens when you wipe a hard drive which has a partition that is mounted? I was using ubuntu 9.10 live CD but I had one partition on a hard drive mounted. Then, I started to wipe the entire hard drive with random characters using dd. Only later I realized that I hadn't unmounted that partition. what could have happened? Could the Live CD have been damaged?
#The mounted partition cannot be worked on so the partition mounted is the way it was.
#The live cd is fine.

---

### Post by jsvidyad on 2010-12-22
But, I am unable to see any of the files in that mounted partition. Anyway, my main concern is that the LiveCD might have become damaged. I just wanted to wipe that hard drive clean. I had forgotten about the mounted partition.

---

### Post by efflandt on 2010-12-22
dd directly to the device does not have the safeguards of more advanced tools. So you likely overwrote that mounted partition (and any partition table), rendering that partition unrecoverable, if you wrote enough to the drive to overwrite it with random gibberish.

That would not do anything to a live CD.  It would not even do anything to live iso bootable from USB flash or hard drive you were running from, assuming the drive you wiped was some other drive.

To reuse that drive you might want to write 1 GB of zeros to it (if=/dev/zero) to avoid misinterpretation. Then use gparted to create an msdos partition table (you need some type of partition table before you can create any partitions on it).

---

### Post by hello2012 on 2010-12-23
[FONT=Times New Roman][SIZE=3]Do not think the operation about wipe hard drive permanently is how complex to finish, you can try to use 3rd partition software—[free partition manager]("http://www.extend-partition.com/free-partition-manager.html") can wipe hard drive for you, I think.[/SIZE][/FONT]

---

