---
title: "CD contents not appearing anywhere ... ?"
date: 2009-10-17
forum: General Help
---

### Post by Bucky Ball on 2009-10-17
Hi all,

I insert an audio CD, Sound Juicer pops up as it should, but if I close it, there is no CD icon and the CD vanishes; not it Places, /dev/scd0 or /media/cdrom0. The contents are untraceable. The only way to get back to it is to re-insert the disk and get Sound Juicer to pop up with the tracks again. Here is the line from my /etc/fstab file:

```
/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0

```

Immediately after inserting a cd with Sound Juicer still open:

```
bucky@studiobox:~$ dmesg | tail
[ 1537.601269] end_request: I/O error, dev sr0, sector 1016756
[ 1537.603231] end_request: I/O error, dev sr0, sector 1017412
[ 1537.605228] end_request: I/O error, dev sr0, sector 1016388
[ 1537.606872] end_request: I/O error, dev sr0, sector 1016164
[ 1537.608932] end_request: I/O error, dev sr0, sector 1017404
[ 1537.610560] end_request: I/O error, dev sr0, sector 1016380
[ 1537.612254] end_request: I/O error, dev sr0, sector 1016156
[ 1537.613917] end_request: I/O error, dev sr0, sector 1248
[ 1537.615823] end_request: I/O error, dev sr0, sector 1024
[ 1537.615922] UDF-fs: No partition found (1)
```

I have done quite a bit of hunting and this problem seems to be known but I couldn't find anything that worked for me.

---

