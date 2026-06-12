---
title: "Corrupt Partition in Ubuntu 11.10"
date: 2012-06-12
forum: General Help
---

### Post by pawanthegunner on 2012-06-12
I was trying to install Windows XP along side Ubuntu 11.10 which I already had. I Followed some instructions and used GParted from my 10.04 live CD because the 11.10 disk does not have it.

I shrunk the partition and created a new ntfs from the unallocated space. But when I applied the changes, GParted threw some error at the last step of completing the shrinking.
Now when I again refreshed Gparted, it showed that the partition had been shrunk and so I went and created the ntfs from the unallocated space. All seemed well.

But when I tried to reboot into ubuntu, the BusyBox comes up. this had happened before so from the live CD I ran 
```
e2fsck -v -f -y /dev/sda1
```
which gives this result,
```
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 11496507 blocks
The physical size of the device is 11496259 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes
```

So, Is my partition gone? Is there a way to recover it or I have to do a clean install?

---

