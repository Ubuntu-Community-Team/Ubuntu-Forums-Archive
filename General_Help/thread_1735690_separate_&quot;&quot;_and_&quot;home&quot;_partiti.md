---
title: "separate &quot;/&quot; and &quot;/home&quot; partitions"
date: 2011-04-21
forum: General Help
---

### Post by dragonfly41 on 2011-04-21
Having had to reinstall ubuntu_10.10 .. I've decided to setup two partitions as advised in other threads

/dev/sda7      10 GB    for ubuntu "/    "
/dev/sda8      30 GB    for ubuntu "/home"

The first partition is now working ..

but I'm not sure if I must now install ubuntu _a second time_ in /dev/sda8 

selecting "/home" as the mount point

and do I set "/dev/sda7" as the bootloader as in the first partition?

Thanks

---

### Post by blueridgedog on 2011-04-21
When you did the install, did you elect to format and mount sda8 as /home?

---

### Post by lithopsian on 2011-04-21
You don't need to install twice, but it you have just installed and /home is not mounted on /dev/sda8 then the easiest way to fix it might be to reinstall.  You can copy everything to /dev/sda8 and remount /home there, but it isn't as simple as you might expect.

---

### Post by oldfred on 2011-04-22
How to move /home, but if your install has no effort on configuration, then it may be quicker to reinstall, unless you want to learn about copying files, mounting partitions, & editing fstab.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Your /boot is inside the / (root) partition. But to get it to boot you have to install the grub2 boot loader to the MBR of the drive - sda or whichever drive you installed to, not the partition sda7.

---

### Post by drs305 on 2011-04-22
I'm a fan of Ivan K's method posted by *oldfred*. Once the /home partition is made, it is a very easy process with simple commands. 

I used this method fairly regularly to create a separate /home just before installing a new release to bring bring over all my /home configurations.

---

### Post by dragonfly41 on 2011-04-22
Thanks for the advice.
I can see where I went astray in first trying this.
I should have set up _both_ partitions before hitting "install now".

...

Reading the replies above  I've now opted for a fresh installation since I had only recently tried to reinstall.

I can see that if /home has been populated with a number of installed applications it might be better to move /home from one partition to another as oldfred and drs305 suggest.

But I had just finished a fresh installation with no user profiles of any significance and it seemed easier to just reinstall into two partitions.

I have a separate ntfs partition reserved for sharing common data between ubuntu and Vista and backups.

I have a grub2 loader in the MBR of the drive sda (from a previous installation) but when installing ubuntu I set as "device for boot loader installation" - /dev/sda7.   Seems to boot o.k. from Grub2 into generic linux (35.22 whatever that is).

My remaining question and I can then mark this as solved is ..

If I do have to reinstall ubuntu again do I go through the same process mounting into two separate partitions but this time _not ticking format_ in "/home" mount - to retain user profiles?

Thanks again for the advice.

---

### Post by drs305 on 2011-04-22
> **dragonfly41 said:**
> If I do have to reinstall ubuntu again do I go through the same process mounting into two separate partitions but this time _not ticking format_ in "/home" mount - to retain user profiles?


That is correct. Designate the /home partition but do NOT tick the box to format it. In that way the partition will be set up as /home but will keep existing configurations to the extent possible.

Regarding Grub2: It sounds like you have it set on a partition. While this works, it is more subject to breakage. Unless you have a reason not to, it is preferable to have it installed in the MBR.

It is a simple process if you are running from your normal installation:
```
sudo grub-install /dev/sda
```

Happy Ubuntu-ing !

---

