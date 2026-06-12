---
title: "Device Label help needed"
date: 2010-01-20
forum: General Help
---

### Post by chupalo on 2010-01-20
I have three internal hard drives which I have successfully configured to mount during boot up via fstab.  The labels for the devices show up as "500 GB Filesystem".  Since I have three of them I would love to change the labels to be more descriptive.

Does anyone know how to change the label?  I've been hunting around but haven't found a successful solution.

Thanks

FJ

---

### Post by nothingspecial on 2010-01-20
It depends on what file system they are.

Elaborate please :D

---

### Post by chupalo on 2010-01-20
They are all NTFS.  What more can I tell you?

Thanks

FJ

---

### Post by nothingspecial on 2010-01-20
First

```
sudo fdisk -l
```

From the output, try to know which drive is which.

Then unmount them all.

```
sudo apt-get install ntfsprogs
```

Then

```
sudo ntfslabel /dev/sd[COLOR="Red"]??[/COLOR] new-name
```

substitute the red question marks for the actual partition, discovered with fdisk, and substitute new-name for the name you want to give the drive.

---

### Post by chupalo on 2010-01-20
Thanks.  I'll try this right now.  Do you know where the label "500 GB Filesystem" is coming from?

---

### Post by sisco311 on 2010-01-20
In Ubuntu 9.10 (Karmic) you can use palimpsest (System -> Administration -> Disk Utility) to change the label of the partitions.

---

### Post by nothingspecial on 2010-01-20
> **sisco311 said:**
> In Ubuntu 9.10 (Karmic) you can use palimpsest (System -> Administration -> Disk Utility) to change the label of the partitions.

This is true.

But that is one application I do not like.

---

