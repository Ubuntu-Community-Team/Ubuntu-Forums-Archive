---
title: "Cannot get cachefilesd to work"
date: 2010-05-30
forum: General Help
---

### Post by el_rico on 2010-05-30
Hello,

I'm trying to set-up cachefilesd to improve accesses to my home server (NFS). But the cache is not use. Here is what I've done.
/etc/cachefilesd.conf:
```
dir /fscache
tag mycache
brun 20%
bcull 10%
bstop 5%
frun 20%
fcull 10%
fstop 5%
```
/dev/sda2 is mount at /fscache with user attributes enabled:
```
/dev/sda2 on /fscache type ext4 (rw,user_xattr)
```
The daemon starts without reporting any error (and is actually started). I've mounted a NFS volume with the fsc option:
```
sudo mount 192.168.1.1:/home -o fsc toto/
```
```
192.168.1.1:/home on /home/eric/toto type nfs (rw,fsc,addr=192.168.1.1)
```
But no file is cached (no space is taken on the dedicated partition).

Any idea?

Thanks!

---

### Post by el_rico on 2010-05-30
It seems that 'fsc' option is not correctly taken into account. The option is indeed listed for the mount:
```
192.168.1.1:/home on /home/eric/toto type nfs (rw,fsc,addr=192.168.1.1)
```
 but from /proc/fs/nfsfs/volumes it reads:
```
NV SERVER   PORT DEV     FSID              FSC
v3 c0a80101  801 0:23    f0a51acaba995a8:  no 
```

---

### Post by el_rico on 2010-06-01
I've just tried with nfs4: same problem, fsc option seems to be simply ignored.

---

### Post by el_rico on 2010-06-01
OK... From the kernel (Ubuntu official) config file:
```
# CONFIG_NFS_FSCACHE is not set
```

Why is this feature not enabled by default?

Answer here: [https://lists.ubuntu.com/archives/kernel-team/2009-September/007261.html](https://lists.ubuntu.com/archives/kernel-team/2009-September/007261.html)

---

