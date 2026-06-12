---
title: "Don't have permission to mount floppy drive"
date: 2009-11-20
forum: General Help
---

### Post by FireFighter on 2009-11-20
When I click on Places>Floppy, the drive starts and stops quickly. In terminal, if I type: "/dev/fd0" I get: bash: "/dev/fd0: Permission denied"
Now, if I type in terminal: "sudo /dev/fd0" I am prompted for a password and after entering that, a floppy icon appears on the desktop and I can open it.

I went to Places>Computer>FileSystem>media. I have a floppy and floppy0 listed. When I right click on either of them and then click on Properties>Permissions, I see that root permissions are listed and I can't/don't know how to change that.

Can someone help me with this? Use my floppies! Would love to set it up to go to Places>Floppy and all open up. I have seen other post, but it seemed that their problems were not a permission issue.:confused:

Sorry, I am using Ubuntu 9.10 32bit and the floppy is internal

---

### Post by fancypiper on 2009-11-20
You may not belong to the group that has permissions.  Try adding yourself to the floppy group.

System>Administration>Users and Groups

The mount command goes:

mnt /dev/<your device> <your mount directory>

So, the command to mount it would be something like:

mnt /dev/fd0 /media/floppy

To give yourself mounting permissions, you will need to edit /etc/fstab.  I don't have a floppy, so I can't give you the exact stuff you need in /etc/fstab, but I am sure a quick board search will find you an exact answer.

See:
man mnt
man fstab

---

### Post by FireFighter on 2009-11-20
This is what is in my fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=b21cc84f-aae0-4064-94cd-136cf4560091 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1a1a9a50-4fc4-4658-94bf-d846b825dbae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Just an update. I'm going back to what has been super stable and rock solid for me; 8.04LTS. I will try again when the next LTS comes out. Boy, I thought that the struggles were pretty much over in Ubuntu for me; I guess I have been spoiled by the 8.04 version. Thanks for the reply!

---

