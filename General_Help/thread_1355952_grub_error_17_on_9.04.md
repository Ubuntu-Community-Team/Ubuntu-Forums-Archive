---
title: "grub error 17 on 9.04"
date: 2009-12-15
forum: General Help
---

### Post by konsta82 on 2009-12-15
I have error 17 on startup. Tried to reinstall grub on hd(0,5) but nothing changed. This is maybe because my friend messed something up with ghost on windows partition. Hardware is ok , bios looks fine. Any suggestions please ?

---

### Post by oldfred on 2009-12-15
Did partitions get renumbers or UUID's get copied so you have duplicate UUIDs? Copying partitions is the only way to create a duplicate UUID which can cause big problems.

[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

---

### Post by konsta82 on 2009-12-15
there is problem with uuid , this is how fstab looks like (weird)

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0


I'll try to find old version , maybe I have some backup

---

