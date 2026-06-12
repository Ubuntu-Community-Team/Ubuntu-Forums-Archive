---
title: "moving tmp directory"
date: 2012-02-28
forum: General Help
---

### Post by tryingnow on 2012-02-28
Hi .. I was wondering if there was a temporary way of moving my tmp directory to an external drive .. while i sort out a large file ..

I'm a real noob so I will need a spoonfeed instruction on the method ...

Thanks ahead of time ..

---

### Post by Lars Noodén on 2012-02-28
Yes you can mount an external drive as /tmp, that would be the way to do it.  However, there are probably some needed files there if you are working on a live system and using graphics.  So I would mount it on /mnt first, back up the files from /tmp to /mnt using rysnc or tar, then unmount and re-mount on /tmp

---

### Post by dcstar on 2012-03-01
> **Lars Noodén said:**
> Yes you can mount an external drive as /tmp, that would be the way to do it.  However, there are probably some needed files there if you are working on a live system and using graphics.  So I would mount it on /mnt first, back up the files from /tmp to /mnt using rysnc or tar, then unmount and re-mount on /tmp

The /tmp folder has special permissions and requirements if mounted outside of the root partition.

You need to search out the specific threads that already exist on this subject.

---

### Post by Lars Noodén on 2012-03-01
The permissions for /tmp should be 1777

---

