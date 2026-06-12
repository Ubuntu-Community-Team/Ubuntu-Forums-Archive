---
title: "Join Free Space on 2 Different drives (EEEPC with 2 SSDs)"
date: 2011-12-11
forum: General Help
---

### Post by Krazy_Kaos on 2011-12-11
I have an** eeepc 901** that has **2 SSD** drives **4 GB and 8 GB**.

I Installed ***"Ubuntu 10.04 LTS - the Lucid Lynx"***, and I'm very happy with it.

My only problem is that If I go to my **home/** or **"File System"**  I only have 168MB, but if I go to **"16 GB File System"** (mounted in /media/) I have 8.4 GB.

My question is, Is it possible to **join** (something like **unpartitioning**, if that's even a word) the 2 disks?

Or is it possible to put some parts of linux on one disk and others on the other?

I would like to avoid having to reformat it.

---

### Post by carranty on 2011-12-11
I'm a little unclear on how your partitions are set up on your computer, can you run

```
df -h 
```

in a terminal and post the output so I've a better idea. Note, if you've any external drives/USB sticks etc please remove them before running the above.

---

### Post by Krazy_Kaos on 2011-12-11
> **carranty said:**
> I'm a little unclear on how your partitions are set up on your computer, can you run

```
df -h 
```

in a terminal and post the output so I've a better idea. Note, if you've any external drives/USB sticks etc please remove them before running the above.

This are the results:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.5G  2.8G  606M  83% /
none                  493M  272K  493M   1% /dev
none                  497M 1000K  496M   1% /dev/shm
none                  497M   88K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sdb1              15G  5.7G  8.4G  41% /media/9c9235be-7475-4448-9b05-b9222dce7660

```

---

