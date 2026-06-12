---
title: "Samba doesn't report correct disk quota on subfolders"
date: 2009-11-14
forum: General Help
---

### Post by sbw87 on 2009-11-14
Hi there,
I've just noticed a problem with Samba server (Ubuntu 9.10) and would like to know whether there is an appropriate setting, e. g. in the smb.conf or in some other config file.

The problem is as follows: The directory I shared using samba contains a number of subdirectories which are connected to mounts on another hard drive with more disk space. Samba, however, only transmits the free disk space of the top share directory to clients accessing such a subdirectory to my Windows clients (or is this a Windows issue?).
Is there a way to make Samba output the correct disk quota for each subdirectory of a share? Or do I have to define individual shares for each of those subfolders (this works perfectly for me, but, of course, is much more confusing).

Thanks
s

---

