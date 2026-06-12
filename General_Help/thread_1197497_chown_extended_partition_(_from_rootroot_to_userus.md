---
title: "chown extended partition ( from root:root to user:user )."
date: 2009-06-26
forum: General Help
---

### Post by credobyte on 2009-06-26
How secure ( in the meaning of data loss, mounting, etc. ) it is to chown my extended partition ( not a separate folder ) from **root**:**root** to **user**:**user** ?
By default it's owned by root and I don't want it to be so .. I need to use it all the day long.

---

### Post by mk1w86 on 2009-06-26
I assume you want to change the ownership of the mountpoint of the partition.  To do that run:

```
chown user:user /mnt/mountpoint
```

with /mnt/mountpoint being where your partition is mounted.  This should allow you full access to the partition as user.

> How secure ( in the meaning of data loss, mounting, etc. ) it is to chown my extended partition

If the partition only contains your data and not system files it should be fine the allow user full access to it by the above method. :)

---

### Post by dka on 2009-06-26
> **mk1w86 said:**
> I assume you want to change the ownership of the mountpoint of the partition.  To do that run:

```
chown user:user /mnt/mountpoint
```

with /mnt/mountpoint being where your partition is mounted.  This should allow you full access to the partition as user.



If the partition only contains your data and not system files it should be fine the allow user full access to it by the above method. :)
I agree, if you simply want to change ownership of the mount point run the above command.  If the partition ONLY contains your private/personal data and no system or application data you can do a (chown -R ) and that will recursively change all files and folders under that mount point to user:user. 

Remember with any recursive command, think before you type.

---

### Post by jpc2769 on 2009-07-29
> **mk1w86 said:**
> I assume you want to change the ownership of the mountpoint of the partition.  To do that run:

```
chown user:user /mnt/mountpoint
```

with /mnt/mountpoint being where your partition is mounted.  This should allow you full access to the partition as user.



I tried to do the above command for a partition and it said I am not allowed, even though I did it with "sudo".  Why can't I do this?

Thanks for any help you can provide.

Jason

---

### Post by merlinus on 2009-07-29
What is the filesystem, partition, and mountpoint?

---

### Post by drs305 on 2009-07-29
Edit: Saw the command but not your comment! You did use the correct mount point, didn't you. Please give us the exact error message.

You have to use *sudo* since the files are initially owned by root,

```

sudo chown -R yourname:yourname /mnt/mountpoint

```

---

