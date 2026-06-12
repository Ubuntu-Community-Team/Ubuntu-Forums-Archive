---
title: "Help mountain sdb5?"
date: 2011-02-08
forum: General Help
---

### Post by Vhince2 on 2011-02-08
I've had installed my new Ubuntu onto my 500 GB Seagate.
Before I done any of that, my old Ubuntu I installed was installed 
into my laptop hard drive. It stopped working cause it couldn't
find  /ubuntu/disks/root.disk something like that.

I'm right now using Ubuntu, and I was wondering if anyone knew how to mount my sdb5...


```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60242   483890176   83  Linux
/dev/sdb2           60242       60802     4494337    5  Extended
/dev/sdb5           60242       60802     4494336   82  Linux swap / Solaris
```

Currently using sdb1 ,  I want to mount sdb5 so I could get my old files back. How do I mount it ?

---

### Post by dcstar on 2011-02-08
> **Vhince2 said:**
> I've had installed my new Ubuntu onto my 500 GB Seagate.
Before I done any of that, my old Ubuntu I installed was installed 
into my laptop hard drive. It stopped working cause it couldn't
find  /ubuntu/disks/root.disk something like that.

I'm right now using Ubuntu, and I was wondering if anyone knew how to mount my sdb5...


```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60242   483890176   83  Linux
/dev/sdb2           60242       60802     4494337    5  Extended
/dev/sdb5           60242       60802     4494336   82 ** Linux swap** / Solaris
```

Currently using sdb1 ,  I want to mount sdb5 so I could get my old files back. How do I mount it ?

sdb5 is a **Swap** partition, there is no longer anything to "get back".

---

