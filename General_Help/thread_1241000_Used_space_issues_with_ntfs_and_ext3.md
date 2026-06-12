---
title: "Used space issues with ntfs and ext3"
date: 2009-08-15
forum: General Help
---

### Post by tjb_15 on 2009-08-15
I am backing up my data in two place and the I'm going to switch my main copy to ext3. 

sda4 = Temporary backup space (ext3)
sdb1 = Original location (ntfs)
sdc1 = Normal backup (ntfs)

I copied every thing from sdb1 to sda4. Then I copied it from sda4 to sdc1. 

When I select all the files and go in to properties on each  I get this:

sda4 = Contents: 74,**680** items, totalling 266.1 GB
sdb1 = Contents: 74,**762** items, totalling 266.1 GB
sdc1 = Contents: 74,**680** items, totalling 266.1 GB

In gparted I get this for used space:
```

          Size       Used       Unused
sda4 =    420.34     273.40     146.94
sdb1 =    596.17     266.46     329.71
sdc1 =    465.76     266.44     199.32

```Not really sure why sda4 is using 273.40GB. It is a new partition that I made last night for backing up sdb1.

Are there files that Linux doesn't see from windows partitions? Also, should I convert from ntfs to ext3 on my data drive? I don't think I'm going back to windows any time soon..

Thanks,
TJB

---

### Post by dlmarti on 2009-08-15
Could it be that there are a lot of little files?
Even if a file is only a few bytes it still takes up at least a block, which is probably 4K

---

### Post by tjb_15 on 2009-08-15
I found the problem.. It didn't copy a folder completely. Which would have been bad because it was my firefox profile that has all of my bookmarks. Now they match file wise, but not used space in gparted. I'm not going to worry about it too much because when I highlight all of the folders on all three drives and in properties they all have the same file size... 

Thanks,
TJB

---

