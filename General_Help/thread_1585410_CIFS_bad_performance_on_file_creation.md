---
title: "CIFS bad performance on file creation"
date: 2010-09-30
forum: General Help
---

### Post by jimmydini on 2010-09-30
I am experiencing poor performance when mounting windows share with cifs.
Such poor performance occur only in the creation of files on the share but not in the rewrite.

This is what i do:
```

#mount -t cifs -o guest,user=<user> //153.9.200.2/winshare /mnt/winshare/
# time dd if=/dev/zero of=/mnt/winshare/b.avi bs=1024 count=10000
10000+0 records in
10000+0 records out
10240000 bytes (10 MB) copied, 25.7762 s, 397 kB/s

real    0m25.910s
user    0m0.091s
sys     0m1.508s
# time dd if=/dev/zero of=/mnt/winshare/b.avi bs=1024 count=10000
10000+0 records in
10000+0 records out
10240000 bytes (10 MB) copied, 1.98109 s, 5.2 MB/s

real    0m2.041s
user    0m0.013s
sys     0m0.244s
```as you can see, in rewriting the same file i reach better  transfer rate.

I'm using FC13 
kernel 2.6.33.3-85.fc13.i686.PAE
Cifs kernel module ver.  1.62

I performed the same test with a Ubuntu live distro (ubuntu-9.4-desktop) NOT experiencing such problem and with another Ubuntu (ubuntu-10.04.1-desktop) that have the same problem.

I'm asking myself if i am in the case of this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471512)

and if i'm experiencing a kernel bug.

Thanks

---

### Post by jimmydini on 2010-10-02
No answers ?

---

