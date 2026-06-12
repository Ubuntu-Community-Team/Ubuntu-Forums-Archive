---
title: "How to reinstall while preserving /home?"
date: 2010-05-01
forum: General Help
---

### Post by Kurtosis on 2010-05-01
Hi all, currently my installation is on sda1, while /home is on sdb1.  I'd like to wipe sda1 and reinstall Ubuntu 10.04 from scratch.

Can I just run the 10.04 installer, reformat sda1, install 10.04 over it, then follow [a guide]("http://www.ibm.com/developerworks/library/l-partplan.html") to remount sdb1 to /home (and chown the new /home)?

Or is there more to it?

---

### Post by gadolinio on 2010-05-01
As far as I know, that can be done; I even think that's the point of having your home folder in a separate partition. When you create a new user in the new installation, you can choose which will be its home folder; you can choose /media/mountpoint_for_sdb1/home/username, for example. You can also use the home directory in sdb as a backup, and then simply copy it to the new user's home.

---

### Post by Pingster on 2010-05-01
That's basically what I did.  When you get to the partition options screen select the third option (Manual or something like that).
Select your /home partition, click edit, and mount as /home.  The rest is pretty much self-explanatory.

---

### Post by srs5694 on 2010-05-01
The guide to which you pointed is intended for people who don't already have separate /home partitions. Your situation is simpler:


[list=1]
[*]Start the installation.
[*]Select advanced (or "manual;" I don't recall precisely what it's called) partitioning.
[*]Locate and select your current root (/) partition. Click the "Change" button (I think that's what it's called, but I could be mistaken), select root (/) as the mount point, and check the option to create a new filesystem (or "format" the partition, if that's the terminology they use).
[*]Locate and select your current /home partition. Click the "Change" button, select /home as the mount point, and be sure that the "create a new filesystem"/"format" option is *not* selected. Repeat: Be sure you do *not* create a new filesystem on this partition!
[*]Continue with the installation.
[/list]


That's all there is to it, unless you created multiple accounts originally or use a new username this time around. Mucking with the mount points and home directory locations as gadolinio suggests should not be necessary, at least not if you use the same username on your new install as you did on the original install. If you did create multiple accounts originally or if you change your username, you may have multiple subdirectories in /home that you may need to integrate or rename, but you can post again if you run into problems with that.

---

### Post by Kurtosis on 2010-05-03
> **srs5694 said:**
> [list=1]
[*]Start the installation.
[*]Select advanced (or "manual;" I don't recall precisely what it's called) partitioning.
[*]Locate and select your current root (/) partition. Click the "Change" button (I think that's what it's called, but I could be mistaken), select root (/) as the mount point, and check the option to create a new filesystem (or "format" the partition, if that's the terminology they use).
[*]Locate and select your current /home partition. Click the "Change" button, select /home as the mount point, and be sure that the "create a new filesystem"/"format" option is *not* selected. Repeat: Be sure you do *not* create a new filesystem on this partition!
[*]Continue with the installation.
[/list]

Perfect directions, worked without a hitch, thanks!  <3 that installer feature.

---

