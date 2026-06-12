---
title: "Duplicity and network folders?"
date: 2010-07-24
forum: General Help
---

### Post by theindustry on 2010-07-24
Hi everybody,

I just installed Duplicity on Ubuntu and got everything working. However, when I try to backup a network samba-connected windows drive, The following occurs:

```
Backup source directory /smb:/windowscomputer/harddrive/folder does not exist.
```Here's how it's formatted in my backup.sh script:
```
duplicity --full-if-older-than 14D --encrypt-key=XXXXXXX --sign-key=XXXXXXX smb://windowscomputer/harddrive/folder s3+http://myS3BUCKET
```What can I do to make this work? I'm kinda stuck right now. Thanks!

---

### Post by robsoles on 2010-07-24
Sounds like you need to mount it using /etc/fstab - have a look at [this post](http://ubuntuforums.org/showpost.php?p=9566270&postcount=6) and be aware that the user 'root' can be replaced with the username you usually use to access this share **and** you will have to put your password in plaintext into the file as well.

Some programs won't play with samba if the share isn't mounted - this is gotten around in gnome by use of a special folder ~/.gvfs but that only has a mounted reference to the share after the user has used nautilus to mount it.

You should probably have a squiz at [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) if you will use /etc/fstab to get your job done.

---

### Post by theindustry on 2010-07-25
> **robsoles said:**
> Sounds like you need to mount it using /etc/fstab - have a look at [this post]("http://ubuntuforums.org/showpost.php?p=9566270&postcount=6") and be aware that the user 'root' can be replaced with the username you usually use to access this share **and** you will have to put your password in plaintext into the file as well.

Some programs won't play with samba if the share isn't mounted - this is gotten around in gnome by use of a special folder ~/.gvfs but that only has a mounted reference to the share after the user has used nautilus to mount it.

You should probably have a squiz at [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) if you will use /etc/fstab to get your job done.

Hi! That made the trick :) Thanks a lot!

---

