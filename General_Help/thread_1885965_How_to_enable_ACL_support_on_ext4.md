---
title: "How to enable ACL support on ext4 ?"
date: 2011-11-24
forum: General Help
---

### Post by pawan613 on 2011-11-24
Hello there.
I'm using Ubuntu 10.10 on ext4 file system and have exported a directory "/home/dbs/exp1/" through Samba on Windows(on VirtualBox).
I need to modify the acls for the files in the above directory both from Ubuntu and Windows.
For linux, I'm using setfacl utility to modify ACLs, but it says that "Operation is not supported". From google I got to know that acl and user_xattr support has to be enabled at the mount point to modify the ACLs
So, can anyone tell me clearly, what should I do to enable ACL support?
My /etc/fstab looks like:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation

UUID=66eeee3e-b860-41b0-abf7-074c0e08420e /               ext4    errors=remount-ro 0       1

#Entry for /dev/sda2 :
UUID=2080E92980E905DE    /media/Data ntfs defaults,uid=dbs,gid=dbs,umask=000,windows_names 0 0

#Entry for /dev/sda1 :
/dev/sda1    /media/Windows_XP ntfs defaults,uid=dbs2,gid=dbs2,umask=000,windows_names 0 0


Please help me! :(
Thanks in advance.

---

### Post by pawan613 on 2011-11-24
I tried:
sudo mount /home/dbs/exp1 -o remount,acl

but it says:
mount: can't find /home/dbs/exp1 in /etc/fstab or /etc/mtab

---

### Post by dragos2 on 2012-05-17
its simple:

Modify /etc/fstab by adding 'acl'
```

UUID=66eeee3e-b860-41b0-abf7-074c0e08420e / ext4 errors=remount-ro,acl 0 1

```

and reboot.

You can additionally install eiciel for graphical ACL edit in Nautilus but its not very intuitive.

Please be aware that POSIX ACL does NOT map exactly to Windows permissions.

In order to achieve strict mapping of the later you need NFS v4 ACL or ZFS,
or play with Samba's more advanced settings for a lossy mapping.

---

### Post by pawan613 on 2012-05-17
Thanks for reply. This modification in /etc/fstab did the trick.

---

### Post by dragos2 on 2012-05-18
> **pawan613 said:**
> Thanks for reply. This modification in /etc/fstab did the trick.

You're welcome :)

Please mark thread as solved, as I saw many questions regarding this.

---

