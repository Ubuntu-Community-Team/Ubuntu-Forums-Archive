---
title: "md5sum differs on copy file/s by nautilus or krusader"
date: 2011-09-18
forum: General Help
---

### Post by masuch on 2011-09-18
Hi,

When I am trying to copy big file/s (from gigabytes to tens of gigabytes) *.ISO file/s or *.vdi files using krusader file manager I have got different checksum by md5sum. If I copy them using nautilus there is problem with *.vdi (tens of gigabytes) in md5sum.

I thought that following could help but it did not:
sudo sync && sudo sysctl -w vm.drop_caches=3 && sudo sysctl -w vm.drop_caches=0

could anybody please explain me what am I doing wrong ?
thanks for any help.

---

### Post by masuch on 2011-10-01
Problem was one out of four memory modules.

---

