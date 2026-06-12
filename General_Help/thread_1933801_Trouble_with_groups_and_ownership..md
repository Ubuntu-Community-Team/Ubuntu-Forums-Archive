---
title: "Trouble with groups and ownership."
date: 2012-03-01
forum: General Help
---

### Post by gclayton on 2012-03-01
Okay, I give up. I have changed my server from an old Dec ALPHA to a shiny new to me DELL 2650. Installed Lubuntu 11.10 with no problems and mounted my RAID 1 setup formated fat32 for my windoze machines. I want to share with samba, but i can't change the group settings after i have mounted it. It is owned by root, and the group is root. I want to change the group to users for my samba shares. I've been running suse for years and after looking through the docs i can't find a better way to do this I am using the command as follows "sudo chgrp -R users /srv/samba/share/stores" . I receive an "operation not permitted" after it appears to change the group settings. I have tried to change ownership as well with same results, as well as breaking down to a single file with the same results. Oh yeah, I'm mounting the drive with "sudo mount -t vfat -w /dev/sdb1 /srv/samba/share/stores"  . Any help would be greatly appreciated, I have run out of ideas, and just keep running the same loop when I'm looking for new information. thank you...

---

### Post by bab1 on 2012-03-01
> **gclayton said:**
> Okay, I give up. I have changed my server from an old Dec ALPHA to a shiny new to me DELL 2650. Installed Lubuntu 11.10 with no problems and mounted my RAID 1 setup formated fat32 for my windoze machines. I want to share with samba, but i can't change the group settings after i have mounted it. It is owned by root, and the group is root. I want to change the group to users for my samba shares. I've been running suse for years and after looking through the docs i can't find a better way to do this I am using the command as follows "sudo chgrp -R users /srv/samba/share/stores" . I receive an "operation not permitted" after it appears to change the group settings. I have tried to change ownership as well with same results, as well as breaking down to a single file with the same results. Oh yeah, I'm mounting the drive with "sudo mount -t vfat -w /dev/sdb1 /srv/samba/share/stores"  . Any help would be greatly appreciated, I have run out of ideas, and just keep running the same loop when I'm looking for new information. thank you...

Windows type file systems (VFAT, FAT32 and NTFS) have no concept of user/group/others.  No chmod will work.  You define the user and group with the mount command.  See the man pages for mount.ntfs.  On Linux you can do this from the terminal like this```
man mount.ntfs
```
Or you can google mount.ntfs.

---

### Post by gclayton on 2012-03-01
Thanx bab1, Thank you so very much. That explains my headache. I was going crazy trying to figure it out..... :)

---

