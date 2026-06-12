---
title: "Picasa can't see 2nd hdd"
date: 2012-03-19
forum: General Help
---

### Post by kurja on 2012-03-19
Google picasa can't see my second hard drive in Tools -> Folder manager, I can only add folders on the system disk. I know there's a way to make it work, I've done it before but can't remember or find the answer... argh. Help?

---

### Post by ajgreeny on 2012-03-19
> **kurja said:**
> Google picasa can't see my second hard drive in Tools -> Folder manager, I can only add folders on the system disk. I know there's a way to make it work, I've done it before but can't remember or find the answer... argh. Help?
Can you just navigate to the disk partition which is probably mounted in the filesystem at /media/*partitionname*

---

### Post by kurja on 2012-03-19
Yes, sure. It's mounted and I can access everything on it, it's just that picasa can't see it's even there.

---

### Post by BertN45 on 2012-03-19
Did you go through File "add folder" and then click the plus on the "/" entry. repeat it for media, your drive folder name, etc

Sometimes the mount point is in Home -> .gvs (you have to use ctr+h to see .gvs). In that case you stuck and have to mount your second drive through fstab and not through e.g. Gigolo.

---

### Post by kurja on 2012-03-20
It is mounted in /media. I can't see it under the "/" entry :^/

---

### Post by kurja on 2012-03-20
ah - found it!!!!!

under the "/" entry afterall, I just needed to dig up the mount point from there. excuse me for my stupidity =D

---

