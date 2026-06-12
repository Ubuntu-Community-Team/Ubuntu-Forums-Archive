---
title: "Captive NTFS almost sorted! Help with fstab config?"
date: 2005-02-05
forum: General Help
---

### Post by EnderWiggin on 2005-02-05
Now the ntfs partitions mount with no troubles, just one niggling thing:

Captive NTFS wrote the partitions to /etc/fstab, as noauto. I changed that to auto, now it does something strange: before I mount anything, I cd to the mount directory. The first time I type ls, it shows nothing [as if the drive isn't mounted yet]. I type ls immediately afterwards, and it displays the drive root directory contents! Yet when I try to cd to any of the displayed directories, I'm told that said directory doesn't exist. Only when I manually mount the [supposedly auto-mounted in fstab] ntfs partition, it works properly.

Am I supposed to make an entry in another file?

Also, [/alternatively?] how do I put a launcher on my desktop so the partition auto-mounts like it does in Knoppix?

---

### Post by Megapearl on 2006-10-04
I'm having EXACTLY the same issue, i can't find out what's wrong here... anyone??

> **EnderWiggin said:**
> Now the ntfs partitions mount with no troubles, just one niggling thing:

Captive NTFS wrote the partitions to /etc/fstab, as noauto. I changed that to auto, now it does something strange: before I mount anything, I cd to the mount directory. The first time I type ls, it shows nothing [as if the drive isn't mounted yet]. I type ls immediately afterwards, and it displays the drive root directory contents! Yet when I try to cd to any of the displayed directories, I'm told that said directory doesn't exist. Only when I manually mount the [supposedly auto-mounted in fstab] ntfs partition, it works properly.

Am I supposed to make an entry in another file?

Also, [/alternatively?] how do I put a launcher on my desktop so the partition auto-mounts like it does in Knoppix?

---

