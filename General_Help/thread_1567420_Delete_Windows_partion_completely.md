---
title: "Delete Windows partion completely"
date: 2010-09-03
forum: General Help
---

### Post by ChaosChris2009 on 2010-09-03
Hi, how do I completely delete the Windows partion using GParted in Ubuntu?

I heard that the boot option for Windows still shows even after deleting the partition using GParted

Any help is appreciated

---

### Post by Smart Viking on 2010-09-03
You launch gparted, and delete the windows partitions(simple as that).
Eventually resize your ubuntu partition(s) so they use the available free space(would need to use a live CD to do that).

About the options in grub remaining thing, i think it would work to simply launch this command:
```
update-grub
```
But i'm not entirely sure. :)

---

### Post by finwake on 2010-09-03
Grub update needs to be run as root:

```
sudo update-grub
```

Also, if you don't want the potential data corruption, nor long wait, nor use of liveCD, that is required to grow your Ubuntu root partition, you can simply delete the Windows files and keep using the 'ntfs' partition.

You can be less lazy and reformat the partition to 'ext4' and use it for data...

---

