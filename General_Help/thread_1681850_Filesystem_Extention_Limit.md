---
title: "Filesystem Extention Limit"
date: 2011-02-04
forum: General Help
---

### Post by ufuser1 on 2011-02-04
Hello everyone,
I've  come to realize that the sda3 ( the /  mount point) is way too small, and so that's why  I have resized my home partition which was taking all the space. Now that I have about 40 gigs of 'unallocated space' I can't seem to extend the sda3 file system. I've used gparted succesfully to shrink the home partition but nothing else. The bar or handles can only be dragged to a certain extent with a maximum amount of 7.53 GiB which is what I have now. How can extend it and make use of that unallocated space? I'm only allowed to extend the home filesystem and nothing else.

here is some info about the partitions with gparted
```

/dev/sda1 ext2 101.94MiB boot
/dev/sda2 linux-swap 258.86 swap
/dev/sda3 ext4 7.33 GiB /
/dev/sda4 ext4 195.31 GiB home
unallocated unallocated 28.23 MiB --- ---
unallocated unallocated 29.81 GiB --- ---

```
some extra info
```

archuser@archws ~ % df -h                                                        
Filesystem            Size  Used Avail Use% Mounted on
udev                   10M  204K  9.9M   2% /dev
/dev/sda3             7.3G  6.0G  898M  88% /
shm                  1004M  1.2M 1003M   1% /dev/shm
/dev/sda1              99M   16M   79M  17% /boot
/dev/sda4             193G   18G  166G  10% /home

```

---

### Post by spaceboy909 on 2011-02-06
Hmm, just taking a guess here, but possibly because your /home part. was resized by moving the end point backwards (the default operation), instead of moving the starting point forwards, which is what you would need, but that also assumes that the sda3 and sda4 parts. are in series (back to back), which isn't always the case.

Gparted should allow you to move the /home start point forward, but that will involve migrating data, and so there is a higher risk of data loss..........it should warn you about that.  As with all partitioning jobs....backup your data first!

---

### Post by mcduck on 2011-02-06
You can't extend the root partition because the /home partition sits between it and the unallocated space. You'll need to move the /home to free some space next to the rot partition, and *then* you can increase it's size.

---

### Post by HermanAB on 2011-02-06
In this case, it may be better NOT to resize the partitions, but rather move the /usr and /var directories to /home partition:

Reboot in single user mode.

Copy /usr and /var to /home:
cp -a /usr /home
cp -a /var /home

Rename /usr and /var temporarily:
mv /usr /usr.old
mv /var /var.old

Make soft links:
ln -s /home/usr /usr
ln -s /home/var /var

Reboot.

Delete /usr and /var:
rm -Rf /var
rm -Rf /usr

La voila.  You now have oodles of space on / and most schtuff is residing on /home.

---

### Post by ufuser1 on 2011-02-07
Thanks everyone, I moved the /home partition and the / mount point is expandable now.

---

