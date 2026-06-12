---
title: "Can't move items to trash..."
date: 2010-12-04
forum: General Help
---

### Post by tajiknomi on 2010-12-04
[SIZE=2]i recently install ***NTFS-Config*** and ***Auto-mount*** my NTFS_partitions... They are now *successfully* mounting in Start-up, but whenever i try to*** remove ***something(within) NTFS partition, the removing item is ***not going to Trash***,its just deleting that item ***permanently***, Any Suggestion?

My fstab :-

     [/SIZE]```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda8 :
UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca    /    ext3    errors=remount-ro    0    1
#Entry for /dev/sda6 :
UUID=32B4D35146D6CA5D    /media/Extra    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda1 :
UUID=71C9C32D0D73D38C    /media/My_Data    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda5 :
UUID=232D470307EF2C88    /media/My_Media    ntfs-3g    defaults,locale=en_US.utf8    0    0
```[SIZE=2]Moreover , the NTFS are now authorized by Root[/SIZE]....

---

### Post by sikander3786 on 2010-12-04
This might help.

[http://ubuntuforums.org/showpost.php?p=5021804&postcount=4](http://ubuntuforums.org/showpost.php?p=5021804&postcount=4)

But make sure to replace vfat in that post to NTFS.

Example:

```
UUID=232D470307EF2C88    /media/My_Media    ntfs-3g    defaults,utf8,umask=007,uid=1000,gid=1000 0 1
```

Good Luck!

---

### Post by tajiknomi on 2010-12-04
> **sikander3786 said:**
> This might help.

[http://ubuntuforums.org/showpost.php?p=5021804&postcount=4](http://ubuntuforums.org/showpost.php?p=5021804&postcount=4)

But make sure to replace vfat in that post to NTFS.

Example:

```
UUID=232D470307EF2C88    /media/My_Media    ntfs-3g    defaults,utf8,umask=007,uid=1000,gid=1000 0 1
```Good Luck!

[SIZE=2]wait..let me try[/SIZE]

---

### Post by cgroza on 2010-12-04
I have the same problem. Didn't bother with it but I sure want to fix it!

---

### Post by tajiknomi on 2010-12-04
[SIZE=2]Thanks very Much....its absolutely works :guitar:[/SIZE]

---

### Post by sikander3786 on 2010-12-04
You are Welcome :-)

Glad to know it worked for you.

Don't forget to mark the thread Solved ;-)

@cgroza: It worked for **tajiknomi**, it might work for you also. Keep us posted :-)

---

