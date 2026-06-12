---
title: "Partitions in Pendrive"
date: 2012-06-08
forum: General Help
---

### Post by abhicool.indya on 2012-06-08
I have made 2 partition in my 8GB pendrive.

1. 2GB Ext4 Ubuntu liveUSB
2. 6GB NTFS

I am able to read both partition in ubuntu but I am not able to read any partition in windows. 

TIA.

---

### Post by wilee-nilee on 2012-06-08
> **abhicool.indya said:**
> I have made 2 partition in my 8GB pendrive.

1. 2GB Ext4 Ubuntu liveUSB
2. 6GB NTFS

I am able to read both partition in ubuntu but I am not able to read any partition in windows. 

TIA.

Windows will only read the first partition, so it has to be a fat or ntfs, with the ext second.

Windows has to see a external to read through other partitions.

---

### Post by abhicool.indya on 2012-06-08
> **wilee-nilee said:**
> Windows will only read the first partition, so it has to be a fat or ntfs, with the ext second.

Windows has to see a external to read through other partitions.

Thanks a lot. Working fine now.

---

### Post by wilee-nilee on 2012-06-08
> **abhicool.indya said:**
> Thanks a lot. Working fine now.

No problem I discovered this in the same way. ;)

---

