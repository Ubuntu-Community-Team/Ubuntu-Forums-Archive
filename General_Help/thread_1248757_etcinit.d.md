---
title: "/etc/init.d"
date: 2009-08-24
forum: General Help
---

### Post by AnarchyMaster on 2009-08-24
I changed my ssh entry in /etc/init.d to run a program but i forgot to put a & after the entry so when my laptop boots it stops booting and just runs and shows me the output of the program ( it has a loop so it never stops ), is it possible to boot the pc and stop it initialising the scripts in /etc/init.d or make it ignore a specific one?

Thanks

---

### Post by XCan on 2009-08-24
Hmm, I guess safe mode doesn't work for you. However, if you insert the live cd you should be able to modify your init.d file through it.

---

### Post by Slim Odds on 2009-08-24
> **XCan said:**
> However, if you insert the live cd you should be able to modify your init.d file through it.

That's what I'd do.

---

### Post by MrMerry on 2009-08-24
or just add 'init=/bin/bash' to the kernel boot line in grub and edit from there.

---

### Post by MrMerry on 2009-08-24
and you may need to type

```
mount -o rw,remount /
```

if the filesystem is readonly

---

### Post by bodhi.zazen on 2009-08-24
as it boots, try safe mode. If it locks up, hit Ctrl-C

If that fails, time to break out a live CD.

---

