---
title: "cannot be mounted...Waiting for /dev/disk/by-uuid/(number)"
date: 2011-04-07
forum: General Help
---

### Post by TNtornado on 2011-04-07
I'm a relative Ubuntu newb and I'm trying to troubleshoot my g/f's parent's computer. Just after the Ubuntu splash I get a black screen with the following message
 
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/e348db77-9a31-45a2-82f2-c986cb9bc29a
/tmp: waiting for (null)
swap: waiting for UUID=6e886521-b7c9-4744-b31b-ae942a0f279c
 
 
Thanks for any insight.
 
TN

---

### Post by tredegar on 2011-04-07
Please post the output of the following commands (inside CODE tags, please)
```
cat /etc/fstab
sudo blkid
```

---

### Post by TNtornado on 2011-04-07
sudo blkid results
[URL="http://ubuntuforums.org/misc.php?do=bbcode#code"]```
[/URL] sudo: unable to resolve host (none)
/dev/sda1: UUID="e348db77-9a31-45a2-82f2-c986cb9bc29a" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="6e886521-b7c9-4744-b31b-ae942a0f279c" TYPE="swap"
[URL="http://ubuntuforums.org/misc.php?do=bbcode#code"]
```[/URL]

cat /etc/fstab results
```

#/ was on /dev/sda1 during installation
UUID=e348db77-9a31-45a2-82f2-c986cb9bc29a / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=6e886521-b7c9-4744-b31b-ae942a0f279c none swap sw 0 0 
/dev/scd0  /media/cdrom0 udf,iso9660 user, noauto,exec,utf8 0
[URL="http://ubuntuforums.org/misc.php?do=bbcode#code"]
```[/URL]

---

### Post by tredegar on 2011-04-07
The UUIDs from blkid and fstab match, as they should do.

Is the disk failing? The **smartmontools** package might help you here.

Check the HDD cables.

It might be a good time to check your backups.

---

