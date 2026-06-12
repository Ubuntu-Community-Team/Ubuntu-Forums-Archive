---
title: "External hard drive erorr"
date: 2012-06-28
forum: General Help
---

### Post by vokevybez on 2012-06-28
[FONT=Comic Sans MS][SIZE=2]My external hard drive contained many highly fragmented archives (18 to be exact) since it had a FAT32 file system. So I decided to move the files from the external hard drive to my computer´s hard drive. Then I formatted the external hard drive to ext4 (with Gparted). Thereafter I ran ```
fsck /dev/sdb
``` after unmounting the external hard disk drive. However after I executed the command, I am now unable to write files to the external hard drive unless i´m in root. How do I fix this ? :confused: I would really appreciate the help. [/SIZE][/FONT]

---

### Post by Enigmapond on 2012-06-28
Maybe this will help..

```
sudo chown -R(user name)/dev/sdb
```

---

### Post by vokevybez on 2012-06-29
[FONT=Arial Narrow][SIZE=2]It didn´t work but i found the problem the permissions were all set to root so I opened my file manager in root and changed the group access as well as others access but the owner is still root and i cannot change that even when I  launch the file manager as root. I can now write to the hard disk, but how do i change the owner to root? :-k[/SIZE][/FONT]

---

