---
title: "how to use rsync"
date: 2010-01-27
forum: General Help
---

### Post by oier on 2010-01-27
Hello,
I want to use rsync in order to have a folder synced at startup with my fat32 partition. I figured out how to mount the fat32 partition automatically at startup but I'm failing with the rsync command.
I came across this script but it works only the first time, when there is a new file to sync it fails.
The command:
```
 /usr/bin/rsync -r -t -v --ignore-existing --modify-window=1 /home/folderToBeSynced /home/theMountedPartiton/Folder > ~/rsync.log 
```I get the following errors
```
 default_perms_for_dir: sys_acl_get_file(~/dokument.odt, ACL_TYPE_DEFAULT): No such file or directory, falling back on umask

rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6] 
```Any idea how the right command is? Thanks.

---

### Post by t4thfavor on 2010-01-27
Would something like this work?
rsync -auv /media/300-S/Backups/ /media/300/Backups
                 Source                Dest

---

### Post by gtr32 on 2010-01-27
You could try to add this option:

--chmod=u=rwX

Also, look at the file permissions on the folders that you synced, they could be set so that you have no access to them.

---

### Post by oier on 2010-01-27
Many thanks! The problem seems that all the files in the FAT32 partition are shown as owned by root. Because of that I can't drag and drop or paste files to this partition.
Do you know how I can avoid this? This is my fstab file
```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e2188bd8-e0cb-4e56-a868-560e556620a7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0585a541-d1d5-4732-95da-8a9a1e9cd5bc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sda1
UUID=4268-37EC /home/TheFAT32Partition vfat iocharset=utf8,umask=000 0 3

```
I have tried changing UUID to dev/sda1, puting defaults etc, nothing helps. Has it got something to do with umask maybe?
Thanks,
Because the topic has changed I'm going to open a new thread.

---

