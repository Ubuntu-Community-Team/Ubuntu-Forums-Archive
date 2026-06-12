---
title: "how to save UDF (freenas) to ext3"
date: 2010-01-15
forum: General Help
---

### Post by fabianod30 on 2010-01-15
[SIZE=2]Hello,[/SIZE]
 
[SIZE=2]I would like to change my existing FreeNAS server to a ubuntu server…[/SIZE]
[SIZE=2]My action plan:[/SIZE]
[SIZE=2]- remove the existing HD (1TB of Data) from the server[/SIZE]
[SIZE=2]- insert a new HD[/SIZE]
[SIZE=2]- partitioning the new HD (System partition and Data parition, in ext3)[/SIZE]
[SIZE=2]- configure all services (smb, ftp, ….)[/SIZE]
[SIZE=2]- insert the old freenas HD with the Data[/SIZE]
[SIZE=2]Now the problem is the freenas HD uses UDF filesystem.[/SIZE]
[SIZE=2]Now my questions:[/SIZE]
[SIZE=2]- How can I mount the UDF harddisk to ubuntu?[/SIZE]
[SIZE=2]- Can I simply copy the files from the UDF harddisk the the ext3 disk?[/SIZE]
[SIZE=2]- How to format the UDF disk after saving the files to the ext3 disk?[/SIZE]

---

### Post by kevindt on 2010-01-16
Having just transferred a bunch of picture archives (89 GB!) from a SATA drive that was on a FreeNAS server whose motherboard died, this is what I did:

My FreeNAS drive was formatted in BSD UFS by FreeNAS.  When connected to my multi-booting machine running Ubuntu 9/10, it shows up in disk utility as /dev/sdf1.

I installed the ufs package via Synaptic (which will allow read-only access to most UFS disks).

In terminal I created a mount point for the drive:

```
sudo mkdir /mnt/ufsd
```

then to mount the drive to the mount point used:

```
sudo mount -r -t ufs -o ufstype=5xbsd /dev/sdf1 /mnt/ufsd

```

which mounted it cleanly as a read-only directory that could be copied using the normal methods via command line or GUI to another disk.

When done, unmount the UFS drive

```
sudo umount /mnt/ufsd
```

---

