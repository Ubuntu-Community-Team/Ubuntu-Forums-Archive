---
title: "Configuring fstab properly"
date: 2012-06-13
forum: General Help
---

### Post by IQAndreas on 2012-06-13
From information I have read online, I have been trying to modify [FONT="Courier New"]fstab[/FONT] to fit my needs.

Right now, it works, but as you can see, "My Book" shows up twice in the left bar of Nautilus; the second one is unmountable.

[IMG]http://iqandreas.isbetterthanyou.org/public/ubuntuforums.org/ubuntu-screenshot-my-book-fstab.png[/IMG]

Aside from that minor problem, I have two requirements:
(1) "My Book" needs to be mounted in such a way that it can be used in Samba. (this is currently working with my fstab settings)
(2) "WD Smartware" (the CD) should not be showing up in the launcher. (as you can see in the screenshot, this is not working)

This is how /etc/fstab looks (only the relevant bits):
```
# MyBook
UUID=12C23AD8C23AC031    /media/My\040Book ntfs-3g	auto,users,exec,rw,iocharset=utf8,uid=1000,gid=1000 0 0

# Hide "WD SmartWare"
LABEL=WD\x20SmartWare none udf rw,noauto 0 0
```

Could anyone help me modify fstab correctly?

---

### Post by roelforg on 2012-06-13
> **IqAndreas said:**
> From information I have read online, I have been trying to modify [FONT=Courier New]fstab[/FONT] to fit my needs.
 
Right now, it works, but as you can see, "My Book" shows up twice in the left bar of Nautilus; the second one is unmountable.
 
[IMG]http://iqandreas.isbetterthanyou.org/public/ubuntuforums.org/ubuntu-screenshot-my-book-fstab.png[/IMG]
 
Aside from that minor problem, I have two requirements:
(1) "My Book" needs to be mounted in such a way that it can be used in Samba. (this is currently working with my fstab settings)
(2) "WD Smartware" (the CD) should not be showing up in the launcher. (as you can see in the screenshot, this is not working)
 
This is how /etc/fstab looks (only the relevant bits):
```

# MyBook
UUID=12C23AD8C23AC031    /media/My_Book ntfs-3g    auto,users,exec,rw,iocharset=utf8,uid=1000,gid=1000 0 0
 
# Hide "WD SmartWare"
UUID=<insert_uuid_here> /mnt/smartware auto auto,users,exec,rw,iocharset=utf8,uid=1000,gid=1000 0 0

```
 
Could anyone help me modify fstab correctly?
 
I modded your fstab, though you'll need to run sudo blkid yourself and fill in the uuid of the wd. Also, don't use spaces in the paths when you mount from fstab. You'll need to run 
```

sudo mkdir /mnt/smartware /media/My_Book

```
yourself (the filemanager only looks at stuff mounted in /media, not /mnt).

---

### Post by IQAndreas on 2012-06-13
> **roelforg said:**
> I modded your fstab, though you'll need to run sudo blkid yourself and fill in the uuid of the wd.
I'm afraid it's not giving me a uuid:
```
andreas@tablet-2710p:~$ sudo blkid
/dev/sda1: UUID="54F85300F852DFB2" TYPE="ntfs" 
/dev/sda5: UUID="a0971b1a-a5ac-4a77-8ad7-694985f3e629" TYPE="swap" 
/dev/sda6: UUID="c12c9e57-5250-411d-82e6-ed9a078e304d" TYPE="ext4" 
/dev/sr1: LABEL="WD SmartWare" TYPE="udf" 
/dev/sdb1: LABEL="My Book" UUID="12C23AD8C23AC031" TYPE="ntfs"
```

---

