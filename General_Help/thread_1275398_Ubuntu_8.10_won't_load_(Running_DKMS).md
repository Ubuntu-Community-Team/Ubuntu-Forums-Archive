---
title: "Ubuntu 8.10 won't load (Running DKMS)"
date: 2009-09-25
forum: General Help
---

### Post by gamblor01 on 2009-09-25
Background:

I'm running 8.10 (32-bit) on my system.  It's installed on /dev/sdb3 and I have recently had some problems with /dev/sdb1 -- so much that fsck didn't finish after running for about 16 hours straight, and the partition is completely hosed.

I recently purchased a new drive and will be reinstalling and copying all of my data over (it's installed as sdc).  I have been playing around with trying various commands to copy the data over and "clone" the partition such as:

```

$ sudo -i
# mkdir /media/sdb3
# mkdir /media/sdc1
# mount /dev/sdb3 /media/sdb3
# mount /dev/sdc1 /media/sdc1
# cd /media/sdb3
# tar cf - . | ( cd /media/sdc1; tar xf -)

```That worked to copy everything but when I try to boot up using sdc1 it just hangs when starting CUPS.  I have also tried to copy the entire drive bit for bit:

```

# dd if=/dev/sdb of=/dev/sdc bs=32256

```That failed during the dump after about 20GB were copied.  The drive is 250GB so 20GB isn't a success.


My current problem:

I'm not sure, but the above *may* have something to do with this.  When I try to boot up my sdb3 partition now it just sits there hanging forever on:

> 
Running DKMS auto installation service for kernel 2.6.27-14-generic
Anyone know what that means?

---

### Post by gamblor01 on 2009-09-25
Oh, and I should probably mention that I tried booting up in a live CD and running fsck on /dev/sdb3.  It said it was clean.  I haven't tried forcing the fsck, but if it says it's clean then it is probably OK.

---

