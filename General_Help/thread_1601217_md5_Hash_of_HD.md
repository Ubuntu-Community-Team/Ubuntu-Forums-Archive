---
title: "md5 Hash of HD?"
date: 2010-10-19
forum: General Help
---

### Post by alphaamanitin on 2010-10-19
Hey Guys,

I am in the process of cloning a HD.  Before I wipe the original drive I was wondering if there was a tool to create something like a md5 hash of the entire drive to verify that I have an exact copy.  It does not necessarily have to be an md5 hash and any command line BASH options would work for me as well.

Thanks,

AlphaA

---

### Post by rbc on 2010-10-20
in terminal, try:

sudo md5sum /dev/sdX (replace X with whatever letter represents the drive you want to hash)
Also make sure no partitions on that drive are mounted

---

