---
title: "Turning off Authentications"
date: 2010-01-29
forum: General Help
---

### Post by xhaansx on 2010-01-29
Hey - real quick nooby (I think?) question:

How can I turn off specific authentications? I don't want to have to authenticate every time I mount a different drive (in a different partition). (Because I can't open Mozilla, since it pulls a profile from that partition, without authenticating; and I want to have Mozilla automatically launch on startup, but it can't launch if I need to type my password to gain access to the drive first!).

Many thanks,
xhaansx

---

### Post by hemimaniac on 2010-01-29
well a neat tool for configuring the fstab file for beginers is Storage Manager to get it

sudo aptitude install pysdm

then it is System > Administration > Storage Manager

then you can configure the partitions to defaults (less secure) they will mount automatically at boot time usually in /media/hdx

---

