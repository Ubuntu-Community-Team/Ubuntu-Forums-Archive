---
title: "External Hard Drive Partitions?"
date: 2010-01-03
forum: General Help
---

### Post by ethaniscool on 2010-01-03
Ok. So I recently got a WD MyPassport external hdd with 500gb capacity. I formatted it to NTFS so that it would be more efficient transferring data between my Ubuntu and Win7 dual boot. But now I want know if it is possible for me to create a 100gb FAT32 partition on the external without destroying the data on it.

---

### Post by LinuxRules1 on 2010-01-03
you can resize the ntfs partition with gparted. you can also format the new 100GB partition with gparted. it won't destroy your current information as long as you don't have the drive totally used up. meaning that you have at least 100GB free on the drive.

---

### Post by ethaniscool on 2010-01-03
How would I do that because when I go into gparted and select "Create Partition Table", I get a warning that it will erase all data on the disk.

---

### Post by todak on 2010-01-03
First - Unmount the drive then resize the partition with the data to create an empty 100GB partition. Click apply. Then Create a new primary partition in the empty (unallocated) space and format it as FAT32.

---

### Post by lidex on 2010-01-03
> **ethaniscool said:**
> How would I do that because when I go into gparted and select "Create Partition Table", I get a warning that it will erase all data on the disk.

No. That's not what you want to do. You want to resize. Click on the 500gb partition in the lower pane to select. In the toolbar click the "resize/move" button and you'll be presented with a new window. In the bar at the top click and drag on the right arrow, bringing it to the left until it has reduced the partition by the desired amount. Then click "resize/move" in that window. Back in the first window click "apply".

That will shrink the partition and create free space after it. You can then select that free space and create a new partition from it.

[COLOR="Red"]MAKE SURE the disk is unmounted first![/COLOR]

---

### Post by ethaniscool on 2010-01-05
> **lidex said:**
> No. That's not what you want to do. You want to resize. Click on the 500gb partition in the lower pane to select. In the toolbar click the "resize/move" button and you'll be presented with a new window. In the bar at the top click and drag on the right arrow, bringing it to the left until it has reduced the partition by the desired amount. Then click "resize/move" in that window. Back in the first window click "apply".

That will shrink the partition and create free space after it. You can then select that free space and create a new partition from it.

[COLOR="Red"]MAKE SURE the disk is unmounted first![/COLOR]

"resize/move" isn't an available option. also, when I double click the partition to get more information a warning says that the contents of the disk can not be read.

---

### Post by Leppie on 2010-01-05
i believe that in order to be able to manipulate ntfs partitions the package ntfsprogs needs to be installed first:
```
$sudo apt-get install ntfsprogs
```

---

### Post by ethaniscool on 2010-01-07
Thanks. I got it all worked out.

---

