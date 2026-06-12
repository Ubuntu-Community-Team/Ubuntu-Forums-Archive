---
title: "Can't mount volume after messing up partitions."
date: 2012-01-01
forum: General Help
---

### Post by makko on 2012-01-01
Hi Guys,

So I was installing another distro alongside my Ubuntu/Win7 dual boot.

On installation I was messing around with partitions, resizing etc.. Now I can't mount one of my volumes. Note: I can mount it when I boot into Win7.

Any ideas on how I can fix this?

Is there any output I need to give you here?

Thanks in advance.

---

### Post by fdrake on 2012-01-01
can you post the output of:
```

sudo apt-get install parted
sudo parted -l
sudo blkid

```

---

### Post by Mark Phelps on 2012-01-02
> **makko said:**
> ...Now I can't mount one of my volumes. Note: I can mount it when I boot into Win7.

Since Windows won't mount Linux filesystem partitions, I'm forced to guess that the "unmountable" partition is formatted NTFS or FAT32, right>

In that case, use Win7 to run a CHKDSK on the "unmountable" partition.  To do that, open Computer, right-click on the "drive" you want to check, select Properties, then select Tools, then select Error-checking, then select Automatically fix filesystem errors.

After that, the volume should be mountable in Ubuntu.

---

