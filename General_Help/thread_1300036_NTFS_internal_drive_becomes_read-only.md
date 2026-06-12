---
title: "NTFS internal drive becomes read-only"
date: 2009-10-24
forum: General Help
---

### Post by JPLGuy on 2009-10-24
Hello,

I just recently started getting a problem with my internal NTFS partition. At bootup, the internal NTFS is automounted with read-write privileges, and everything works just fine. When I plug in an external NTFS USB drive, the internal NTFS partition becomes read-only!

I've poked through the system log viewer, and nothing stands out at me. The external drive is recognized and mounted correctly.

I've worked around it by unmounting and remounting the internal partition, but that is really a pain when I just need it to _work_. 

The entries in /etc/fstab reflect either automount or ntfs-3g, with read/write access on. 

The only recent updates I've had are to libpoppler, tzdata, and linux 2.6.8.15 and .16. I'm using 2.6.30 right now.

Anybody else having this problem? Any ideas on how to further diagnose it?

---

