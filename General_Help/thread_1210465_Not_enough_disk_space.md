---
title: "Not enough disk space"
date: 2009-07-11
forum: General Help
---

### Post by n00bhaxor on 2009-07-11
My ubuntu partition has 265 GB free space, yet my home folder says I have 157 MB left, not enough for my music or any other upgrades. I can't add anything. How come I have such little disk space when my partition is large enough?:cry:

See Screenshot

---

### Post by philinux on 2009-07-11
What does this command give you.

```
df -h
```

Have a read here too.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by n00bhaxor on 2009-07-11
```
tyler@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       17G   16G   22M 100% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  108K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  204K  1.6G   1% /dev
tmpfs                 1.6G   76K  1.6G   1% /dev/shm
/dev/sda5             266G   18G  249G   7% /host
lrm                   1.6G  2.2M  1.6G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdg1             299G  113G  186G  38% /media/My Book
/dev/sdh1             7.5G  1.4G  6.1G  19% /media/TYLERS FLSH
tyler@ubuntu:~$ 


```

---

### Post by geirha on 2009-07-11
You have a wubi install, which means Ubuntu is confined to a virtual disk, and the size of that disk was set during the install.

See the wubi guide on the possibility to increase the space available for Ubuntu.
[https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?](https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?)

---

### Post by n00bhaxor on 2009-07-11
Ok, so I opened LVPM, selected resize, then 271360 MB for new size of root.disk. (equivalent to 265GB). 

If I did anything wrong, please tell me.

Thanks for the responses!

---

### Post by n00bhaxor on 2009-07-11
I gave up on that and tried to re-install with Wubi again on XP. This time, I just returned to the previous state- (1 partition, XP, C Drive.) I let Wubi do its thing (no changing settings, left drive on C:, and now it's still the same. 13GB of free space, of the 17GB used to install. 

Should I just try partitioning it from the liveCD? Apparently Wubi isn't working for me.


I also heard something about making the mount point "/". I heard it lets ubuntu access the whole drive. How would I do that?

---

