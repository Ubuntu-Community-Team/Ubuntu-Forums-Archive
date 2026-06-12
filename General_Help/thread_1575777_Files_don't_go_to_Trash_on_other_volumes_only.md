---
title: "Files don't go to Trash on other volumes only"
date: 2010-09-16
forum: General Help
---

### Post by mfearby on 2010-09-16
This has been bugging me for some time but it has just occurred to me that I can only delete files (and have them go to the Trash) if they are on my main volume (a solid-state drive) but files deleted in folders symbolically-linked to a big ol' spinning disk won't go to the Trash. I get this message:

Cannot move file to trash, do you want to delete immediately?

Is there a way to have the Trash work for all mounted volumes?

Here's my /etc/fstab if that contains any clues relevant to anybody:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=be40d08d-16ba-4ff2-9c02-5ece06a07ee3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=6c9abeb4-e22e-470b-ab01-6ca9cb6fa6ee /home           ext4    defaults,nouser        0       2
# swap was on /dev/sdb5 during installation
UUID=11b169f3-fbf8-48df-a7c1-45292da8b423 none            swap    sw              0       0
# Big ol' 500GB drive
UUID=248c9c6e-04a0-4029-9226-d36b7397e9e7	/marc_drive	ext4	defaults,nouser	0	3
```

---

