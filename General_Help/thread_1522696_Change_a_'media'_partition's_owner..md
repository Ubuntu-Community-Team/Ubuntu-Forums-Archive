---
title: "Change a 'media' partition's owner."
date: 2010-07-02
forum: General Help
---

### Post by IBUA on 2010-07-02
I have all my music/photos etc. on a different partition to my Ubuntu and Windows partitions.

However, I can't make any changes like deleting files/renaming etc. because I'm not the partition's 'owner' or i'm not in root.

Can anyone help me to change the ownership of the partition so I can change files from Ubuntu.

Thanks.

(Sorry if this doesn't make sense).

---

### Post by IBUA on 2010-07-02
Nevermind, just needed to use ntfs-config.

---

### Post by WorMzy on 2010-07-02
Is it an NTFS partition? If so, you need to set the owner/group and permissions at mount time. You can add an fstab* entry (or edit the existing one if you've already got one)  for the partition which states who is the owner, which group owns it, and what permissions files have by stating them in the options.

e.g. Here's what my ntfs partition's fstab looks like:
```
# <file system>                           <mount point>             <type>      <options>                                <dump> <pass>
UUID=7A5C94995C94522D                     /media/Terastore          ntfs        user,uid=1000,gid=1000,umask=002,exec,rw 0      0

```


*fstab refers to a file located at /etc/fstab, you'll need to use sudo/gksu to edit it (such as 'sudo nano /etc/fstab' or 'gksu gedit /etc/fstab'

---

