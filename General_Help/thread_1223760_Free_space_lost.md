---
title: "Free space lost"
date: 2009-07-26
forum: General Help
---

### Post by DonLuke on 2009-07-26
Hi, free space of my disk is lost:

doing
$ df -Th

I have:
...
/dev/sdb2    ext4    6,2G    5,8G    0    100%    /


The free space is fixed to 0 while used space keep to be at 100% even if I have 400Mb free as you can see.


I was installing some software and filled the disk, next I stopped and removed 400Mb of that packets, but this problem avoid many applications to write data, for instance gnome desktop settings become reset at each restart.


Anyone can help me?

---

### Post by DaithiF on 2009-07-26
By default 5% of the space on your drive is reserved by linux for system use -- so that in the event of your system running out of disk space there actually is some space available for the system to use to keep itself running.

This most likely accounts for the 400M 'missing' space.

You can confirm this at the terminal by running:

```
sudo tune2fs -l /dev/sdb2

```
look for 'reserved blocks', this number multipled by the 'block size' will give you the number of bytes reserved.

If this partition is a system partition (ie. / is mounted on it), then its not advisable to change the 5%.  If this partition is just used to mount your home directory, then its ok to reduce it.  I'll tell you the command to reduce the 5% but I wouldn't really advise you to use it, unless theres absolutely no other files you can delete to free up space.
```

sudo tune2fs -m X /dev/sdb2

```
where X is a number, e.g. 0, 1, 2 ,3, etc

cheers

---

### Post by HermanAB on 2009-07-26
Ext3 is also a rather inefficient file system.  If you convert that partition to JFS, then you may have 30% free space.

---

