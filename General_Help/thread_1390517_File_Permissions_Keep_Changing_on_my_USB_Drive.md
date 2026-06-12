---
title: "File Permissions Keep Changing on my USB Drive"
date: 2010-01-25
forum: General Help
---

### Post by GenePayne on 2010-01-25
I use a USB drive to store most of my personal and work files, and I use it both at home and at work (two different machines, both running Ubuntu). The drive is encrypted, and is accessed using TrueCrypt (the entire drive is encrypted as a device rather than an encrypted file on the device). The TrueCrypt device is formatted as ext3/ext4.

I have a problem with certain file permissions being changed to read-only (rw-r--r--) after mounting the drive. This happens after I have used it on one computer, and then I mount it on the other. Even though I have been setting write permissions to all (chmod -R a+rw *) to get around this problem, when I mount on the other machine the write access is gone. I don't want to keep manually changing permissions; I would like the file permissions to stay as I set them.

I'm using the same version of TrueCrypt at work and at home. I'm running Ubuntu 9.04 at work, and 9.10 at home.

I do have different usernames on these computers, and I suspect that is the problem (but don't see why this would change file permissions for all users).

Anyone have any suggestions on how to get around this problem, or how to better handle a USB drive on two different machines (with different usernames)?

---

### Post by Surlethe on 2010-01-25
That's funny, because I just installed 9.10, and I can't seem to permanently change the permissions on my flash drive.  To wit, copied directly from command line:

$ ls -l interpolator.f90
-rwxr-xr-x 1 root root 7523 2010-01-22 09:47 interpolator.f90
$ sudo chmod -v a+rwx interpolator.f90
mode of `interpolator.f90' changed to 0777 (rwxrwxrwx)
$ ls -l interpolator.f90
-rwxr-xr-x 1 root root 7523 2010-01-22 09:47 interpolator.f90

---

### Post by GenePayne on 2010-01-26
> **Surlethe said:**
> That's funny, because I just installed 9.10, and I can't seem to permanently change the permissions on my flash drive.  To wit, copied directly from command line:

$ ls -l interpolator.f90
-rwxr-xr-x 1 root root 7523 2010-01-22 09:47 interpolator.f90
$ sudo chmod -v a+rwx interpolator.f90
mode of `interpolator.f90' changed to 0777 (rwxrwxrwx)
$ ls -l interpolator.f90
-rwxr-xr-x 1 root root 7523 2010-01-22 09:47 interpolator.f90

What are the permissions at the mount point of your USB drive? My drive gets mounted at /media/truecrypt1, and this location has full rwxrwxrwx permissions. Maybe yours does not?

---

### Post by t4thfavor on 2010-01-26
Try mounting it on one machine check permissions, then move it to the second and they change, then move back, and see if they are the same as last time.

This will give you an idea of when they are changing, and who is doing it.

I also think this could have something to do with the mountpoint permissions.

---

### Post by GenePayne on 2010-01-29
My current work-around for this problem is to change the owner to myself each time I mount the drive in truecrypt:

```
chown `whoami` /media/truecrypt1
cd /media/truecrypt1
chown -R `whoami` *
```

It seems to work but it takes a little time to recursively change ownership of all files.

I assume this would not be a problem if my username could be the same on both machines.

---

