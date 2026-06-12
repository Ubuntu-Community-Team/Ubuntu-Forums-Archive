---
title: "LVM and an unrelated question"
date: 2006-02-09
forum: General Help
---

### Post by leach on 2006-02-09
Hello, I'm having trouble finding information on how to set up LVM after you install Ubuntu. I'm trying to pool together three 13GB IDE drives none of which hold any of my system files or anything I care about. Is there a tutorial or an app that would help me do this? And while I'm posting, is there a way to install both GNOME and KDE on a system and choose between them at login? Thanks.

---

### Post by RAOF on 2006-02-09
I'm not going to be much help for the first part - I've always done my LVM configuration through the installer.

However, checking out "man pvcreate" & "man vgcreate", you're going to need to:
1) Initialise your drives/partitions for use with LVM.  This uses "pvcreate" - check out the man page
2) Create a volume-group containing all of the drives you've previously set up.  This uses vgcreate (a sample command line here is "vgcreate my-vg-name /dev/hda /dev/hdb /dev/hdc for creating a volume group containing the hda,b,c drives)
3) Create a logical volume (the equivalent of a partition) on your volume-group.  This uses lvcreate.
4) Actually format your logical-volume.  Pick your choice of ext3, reiserFS, whatever.  Check out mkfs.

Secondly, yes.  Install both the kubuntu-desktop & ubuntu-desktop packages, and you'll have a KDE & a Gnome desktop, selectable at login.

---

### Post by leach on 2006-02-09
Thanks, that worked perfectly. One question though, How do I mount and access the new disk?

---

### Post by RAOF on 2006-02-09
[QUOTE=leach]Thanks, that worked perfectly. One question though, How do I mount and access the new disk?[/QUOTE]
Just like you would any other partition, with the exception that the disc-device will be in /dev/mapper.

For example, I can mount my root partition with:
"sudo mount -t reiserfs /dev/mapper/storage-dapper--root <mountpoint>".
(Replacing <mountpoint> with the directory to mount it on - the directory must exist)
But normally you just want an entry in the /etc/fstab file for your partition - eg:
```
/dev/mapper/storage-dapper--root  / ext3 defaults,user_xattr  0 2

```Use the existing entries in your fstab as a guide.

---

### Post by leach on 2006-02-09
Thanks Again

---

