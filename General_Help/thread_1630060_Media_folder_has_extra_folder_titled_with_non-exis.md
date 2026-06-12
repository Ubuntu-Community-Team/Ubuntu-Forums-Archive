---
title: "Media folder has extra folder titled with non-existent partition"
date: 2010-11-24
forum: General Help
---

### Post by Mike_tn on 2010-11-24
Hope this will be easy. Running a dual boot system with Maverick.

When I get my partitions listed in the terminal or in GParted they go up sequentially to **sda7** as they should.  The media folder in my file system shows the other dual boot OS and a data disk partition, both mounted, which is correct. All good.  But there is a third strange folder titled **sda8** however I have no such partition. /etc/fstab shows no sda8 either. When I open /media/sda8, it shows no files, says its empty and lists an empty available space that equals the empty space on the Linux OS partition in which the folder sits. But no pie chart shown, and it belongs to root.  I changed the permission and found I can save files to it.  It wouldn't be so weird if it wasn't labeled sda8. You can't rename it either. Does anyone understand that?

---

### Post by Mike_tn on 2010-11-25
i guess its nothing, I used to have an sda8 partition, so it's just a mount point. I can probably delete in from the terminal.
i read on the forum how someone had several cdrom mount points and no cdrom. they just ignored it.

---

