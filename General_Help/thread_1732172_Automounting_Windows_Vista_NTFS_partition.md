---
title: "Automounting Windows Vista NTFS partition"
date: 2011-04-17
forum: General Help
---

### Post by kvv_1986 on 2011-04-17
Hi, 

I am running Ubuntu 11.04.

I am having trouble automounting the ntfs partition. When I try to access the mounted partition, I get an error saying that I don't have permission to view the files. Also, I am not able to change the permissions as root.

The relevant line on the /etc/fstab file reads:

```
/dev/sda3                                  /media/sda3  ntfs  defaults             0  0  
```

---

### Post by kvv_1986 on 2011-04-17
Never mind. When I restarted the system, it started working out of the blue. Though, it takes a lot longer for startup.

---

### Post by oldfred on 2011-04-18
The more things you mount the longer the startup. And NTFS is a bit slower. But if it is a real long time, it may be time to run chkdsk on your NTFS partition. Ubuntu runs fsck on your partitions after 40 or so boots.

---

### Post by Mark Phelps on 2011-04-18
From personal experience, it's a bad idea to outmount a Vista or Win7 OS partition.  Why? Because if you get an unclean shutdown, that runs the risk of filesystem corruption on the Vista/Win7 partition, and if that happens, you won't then be able to boot into Windows to run chkdsk to fix it.

If you MUST automount, make sure you mount read-only.  That will prevent filesystem corruption but allow you to see the contents of the partition.

---

