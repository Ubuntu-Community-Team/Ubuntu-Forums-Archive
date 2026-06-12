---
title: "which partition is which?"
date: 2012-05-15
forum: General Help
---

### Post by Bre Ntt on 2012-05-15
When choosing to intall ubuntu side by side with windows it gives a partition resize gui, but expects you to guess which is for windows and which is for ubuntu? Every other  install ive done in past installers had them labled if i remember correctly. Whyd that feature go away?

---

### Post by wilee-nilee on 2012-05-15
> **Bre Ntt said:**
> When choosing to intall ubuntu side by side with windows it gives a partition resize gui, but expects you to guess which is for windows and which is for ubuntu? Every other  install ive done in past installers had them labled if i remember correctly. Whyd that feature go away?

Generally I have seen people say the one on the left is windows or OSX.

I will say here after helping a user who did not resize the windows first, and helping them in a large part of today, that resulted in a lot of work for them, it is not worth it.

Resize the windows leaving a unallocated space, if you are running W7 it has a built in partitioner, and reboot it to make sure it works then boot the ubuntu cd and install.

And be sure to fully backup the on board operating system first before doing anything.

If you want to read the thread I will be glad to link you.

---

### Post by bodhi.zazen on 2012-05-15
You need to take care that you understand the syntax Linux uses when referring to partitions.

See : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

If you are not sure, mount the partition and take a look at what is on it.

```
sudo mount /dev/sda1 /mnt
gksu nautilus /mnt
```

The advice to resize windows partitions from within windows is solid advice. You can then leave the free space unpartitioned, and specify your partitions as you install Ubuntu.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Choose to manually specify your partitions.

---

### Post by wilee-nilee on 2012-05-15
> **bodhi.zazen said:**
> You need to take care that you understand the syntax Linux uses when referring to partitions.

See : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

If you are not sure, mount the partition and take a look at what is on it.

```
sudo mount /dev/sda1 /mnt
gksu nautilus /mnt
```The advice to resize windows partitions from within windows is solid advice. You can then leave the free space unpartitioned, and specify your partitions as you install Ubuntu.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Choose to manually specify your partitions.

I just changed mautilus to nautilus for you.

---

### Post by Bre Ntt on 2012-05-16
I'm not that concerned with the data on the windows partition. I basically want a very small XP partition for the sole purpose of watching Netflix without the choppiness caused by VM. 

I guessed wrong and made the Ubuntu partition very small. But I just went with it resized the windows partition and made another partition in gparted, so I guess I'm going to have one of those small partitions for the OS and a big partition for data  that some people used to reccomend way back. Not sure if its best practice, but I don't feel like reinstalling.

Thank you for your help. I acted before reading the advice, but I would have taken your advice. That said, gparted seemed to resize the windows paritition fine, and Windows didn't break---it was a fresh install, so that may have had something to do with it working out OK.

---

