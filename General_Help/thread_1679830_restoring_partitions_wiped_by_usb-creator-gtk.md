---
title: "restoring partitions wiped by usb-creator-gtk"
date: 2011-02-01
forum: General Help
---

### Post by ksatta on 2011-02-01
I accidentally wiped a usb-stick with usb-creator-gtk by selecting a partition and then pressing the "erase disk" button. This seems to be a known problem and the button erases the whole disk as it says, not just the partition.

Well anyway I wasn't sure what was on the partition. There shouldn't be anything important because I always keep backups. Just out of curiosity I tried to get the partitions back. there were two fat32 partitions and then an ext4 partition. Testdisk doesn't seem to find the last partition (ext4) or even the second fat32 that was on the stick. Photorec recovered one mpg file from the stick. There was at least one fsarchiver image on the ext4 partition etc.

Out of curiosity and for similar problems in the future isn't there any way to restore a partition of which there isn't any information in the partition table any more? I would think that it would be possible to detect that an ext4 partition starts here and ends here. Because anything else hasn't been overwritten on the stick except the partition table.

edit: photorec also finds other files when I chose the partition type fat/ntfs/..., but anyway I'd like to know if there is any way to create a new partition table if there is a similar problem in the future.

---

