---
title: "Chrome crashes"
date: 2011-07-02
forum: General Help
---

### Post by rsegoly on 2011-07-02
I am not an experienced UBUBTU user but am using it for over a year on several comuters
On one of them recently  Chrome get crashed all the time, I browse and suddenly the page is gone with error message, similar behavior on Firefox

I searched the web an d someone suggested installing libnss3-dev.
I tried and got this message for libnss3-dbg

E: /var/cache/apt/archives/libnss3-dbg_3.12.9+ckbi-1.82-0ubuntu2_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2

---

### Post by linuxuser12345 on 2011-07-02
Have you tried using Google Chrome's open source counterpart, Chromium?

---

### Post by james_xxx on 2011-07-02
linuxuser12345,

I'm sure that it would be worthwhile to check whether or not Chromium is having the same problems, but the primary focus here is on Chrome. 

I am experiencing the same problem with Chrome in Kubuntu 11.04, not to mention other problems which may or may not be related.

If I run dmesg after Chrome crashes, I see this:

```
$ dmesg | grep segfault
[ 7256.849679] chrome[2926]: segfault at ffffffff ip 00007f9667ff42b6 sp 00007ffffb39c410 error 4 in libglib-2.0.so.0.2800.6[7f9667f94000+ed000]

```

This was occurring for me several times a day on the nettop (with proprietary Nvidia drivers from the repos) listed in my signature, both in google-chrome-stable and now also in google-chrome-beta. I have AdBlock, Google Voice, Voice Search and RSS extensions installed.

---

