---
title: "Permissions on ntfs"
date: 2010-04-06
forum: General Help
---

### Post by duke.tim on 2010-04-06
I am wondering if you can assign permissions on a partition with ntfs as the file system. I am aware of editing fstab and setting some basic permissions. What I am clumsily dictating is can you edit permissions of individual folders for specific users in Linux. I have already tried chmod and such ;)

etc something similar to this ```
[user@computername user]$ sudo chmod 600 directory
```

---

### Post by new_tolinux on 2010-04-06
As far as I know not, as the basics for assigning rights on NTFS are different from the "native" linux-filesystems. For what I know root is assigned to the same default group-id for Administrators under Windows, and the NTFS filesystem is mounted by root.
As a result of that, all users will have root-privileges on NTFS.

The only way I can think of you can block someone, is granting "No access" to the Administrator group in Windows. Although that (again) is equal for all users under Linux. <-- I didn't test that!

---

### Post by karmic-koala on 2010-04-06
Aye, agree with above comment. Linux permissions don't work the same way as Windows so chmod won't do you any good there.

---

### Post by oldfred on 2010-04-06
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by duke.tim on 2010-04-07
I am aware of setting permissions of  the entire partition, is it possible to set different permissions for directories within a NTFS partition.

---

