---
title: "accessing a zfs fool hangs the console"
date: 2012-07-01
forum: General Help
---

### Post by soomon on 2012-07-01
dear forum,

i installed ZFS on my ubuntu 12.04 from the PPA and created my zpool with:

```
$ sudo zpool create zpool0 -m /media/zpool0 raidz /dev/mapper/encrypted1 /dev/mapper/encrypted2 /dev/mapper/encrypted3 /dev/mapper/encrypted3
```

those are encrypted hard drives. i encrypted the wholde disks with LUKS.
that seemed to work.

```
Linux backupserver 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux

```

```
root@backupserver:/home/soomon# zpool status zpool0
pool: zpool0
state: ONLINE
scan: scrub repaired 0 in 0h0m with 0 errors on Thu Jun 28 21:30:19 2012
config:

NAME STATE READ WRITE CKSUM
zpool0 ONLINE 0 0 0
raidz1-0 ONLINE 0 0 0
encrypted1 ONLINE 0 0 0
encrypted2 ONLINE 0 0 0
encrypted3 ONLINE 0 0 0
encrypted4 ONLINE 0 0 0
```

but when i do anything in that directory like "ls -al" or moving a file to it the console i am on hangs. the others continue to work. same result when i connect to it with putty.

i tried the same with gentoo in virtualbox but with not encrypted disks. same result.

i also tried reinstalling ubuntu. nothing helps. 

did anyone have the similar problem?

---

### Post by soomon on 2012-07-03
anyone?

---

### Post by dajhorn on 2012-07-06
The PAE kernel does not satisfy the minimum system requirements for ZoL. 32-bit systems do not have enough virtual address space to reliably stack layers like this.  

Try a 64-bit kernel instead and this configuration should work.

---

### Post by soomon on 2012-07-10
another mysterie solved.
thanks mate!

---

