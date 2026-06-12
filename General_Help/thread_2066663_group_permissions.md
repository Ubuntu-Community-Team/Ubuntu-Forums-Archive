---
title: "group permissions"
date: 2012-10-05
forum: General Help
---

### Post by Drenriza on 2012-10-05
When i plug a usb disk into my ubuntu 12.04 machine. It is mounted with the owner root and the group disk.

On this system i also have a normal user called nice. But nice cannot be allowed to write to the usb disk (copying over folders). Because the user does not have permissions to the usb disk.

So since the usb disk is owned by root and in the group disk (where disk have rw- permissions), i added my nice user to the disk group. But still i cannot get the group permissions to write to the disk.

Anyone who can give their 5 cents so i can copy over folders with my normal nice user?

Thanks on advance.
Kind regards.

**UPDATE**
The disk get the notation /dev/sdb1, owned by root user and disk group.

The mount point is /media/something, which is owned by root and the group root. But it only has root permissions
drwxr-xr-x

My nice user is member of disk and root groups, but the device does not have write permission for the group (root), i cannot write to the disk as nice user.
How can i change this so /media/something get drwxrw---- permissions when it is mounted?

Kind regards.

---

### Post by drmrgd on 2012-10-05
I think it's a simple matter of setting up the appropriate permissions in fstab.  Unless I'm not quite understanding what you are trying to do, you just need to add rw permissions to users in the fstab entry for that device.  Here's a great go to post that I've used quite a lot when I needed help with setting up correct fstab entries:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Drenriza on 2012-10-05
> **drmrgd said:**
> I think it's a simple matter of setting up the appropriate permissions in fstab.  Unless I'm not quite understanding what you are trying to do, you just need to add rw permissions to users in the fstab entry for that device.  Here's a great go to post that I've used quite a lot when I needed help with setting up correct fstab entries:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If i create a fstab entry as follows
```
UUID=328e33c1-8920-4e04-ae03-83cfe0b106ec /media/Nordic ext2 rw 0 0
```

Then i get a error saying
**Unable to mount 32 GB Filesystem**
error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount
/dev/sdb1 on /media/Nordic

> Unless I'm not quite understanding what you are trying to do
I just want usb sticks to start up with 760 permissions.

---

### Post by drmrgd on 2012-10-05
I'm not a terribly great fstabber, but I think you need to add "auto" or "users" to the line in order to allow non-root users to mount the device.  Auto has some other options that you may or may not want.  So, you might decided to explicitly dictate the options rather than use auto.

---

### Post by Drenriza on 2012-10-05
> **drmrgd said:**
> I'm not a terribly great fstabber, but I think you need to add "auto" or "users" to the line in order to allow non-root users to mount the device.  Auto has some other options that you may or may not want.  So, you might decided to explicitly dictate the options rather than use auto.

My fstab now looks like this
```
UUID=328e33c1-8920-4e04-ae03-83cfe0b106ec /media/Nordic ext2 rw,auto,user,noexec,sync 0 0
```

And the device is mounted just fine. But from my normal user (nice) i STILL cannot copy over files to the usb device.

UPDATE
/media/ has 777 permissions, and my nice (normal user) can find create folders and documents in this path.

But when i connect a USB device, i get the following permissions
/media/usb properties says that root has create and delete files, group (root) can list,create/delete,_no access??_ and others has no permissions.

I don't get it.

---

### Post by Drenriza on 2012-10-08
No one?

---

