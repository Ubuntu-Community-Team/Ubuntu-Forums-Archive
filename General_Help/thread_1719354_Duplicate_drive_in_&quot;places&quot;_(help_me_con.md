---
title: "Duplicate drive in &quot;places&quot; (help me configure fstab)"
date: 2011-04-01
forum: General Help
---

### Post by IQAndreas on 2011-04-01
My external harddrive shows up twice in my Places as well as the Nautilus sidebar. Cilcking that extra drive brings up:
> Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

The extra drive appeared after I modified fstab (with help from Google results) in order to allow directories on my external harddrive to be used in apache and other "background" applications.

This is how **fstab** currently looks. (Also, a general question, did I use the right options for my harddrive or is there anything Is should change?)
```
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b2ebd699-03f2-4107-b80f-4cb9e134a2f1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a0971b1a-a5ac-4a77-8ad7-694985f3e629 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

#UUID=12C23AD8C23AC031    /media/My\040Book ntfs-3g  nls=utf8,umask=0222 0    0
UUID=12C23AD8C23AC031    /media/My\040Book ntfs-3g  rw,users,auto,exec,nls=utf8,uid=1000,umask=0000 0    0
```
The commented out line is on purpose. I hate deleting lines in case I need to restore them later (why yes I'm a coder, how did you know?)


I realize this issue has been discussed before, and it's by fixing fstab somehow, but I want to make the changes to fix the problem without messing up my current setup.

It's not causing any problems, I just thought it might look nicer with the extra entry gone. ;)

---

### Post by seawolf167 on 2011-04-01
Your NTFS entry looks ok, though all you really need anymore is the following:

```
UUID=*somenumber*    /path/to/mount/location    ntfs-3g    defaults,locale=en_US.utf8    0    0
```

The first thing I'd try is to unmount both of the devices that are the same

Use *mount *to list your mounted devices

```
mount
```

then use

```
umount
```

and unmount both devices

Then restart and see if you only have the single drive mounted by /etc/fstab on booting.

---

