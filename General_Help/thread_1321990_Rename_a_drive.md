---
title: "Rename a drive"
date: 2009-11-10
forum: General Help
---

### Post by n.hinton on 2009-11-10
After upgrading from Jaunty to Karmic and using Karmic about a week a vfat partition I access was for reasons unknown was renamed from disk-1 to 2D27-07EE.

Question: Is it OK to open ~/media as root and rename 2D27-07EE back to disk-1, or could this action have any adverse effects?

---

### Post by hwttdz on 2009-11-10
That's a bad plan.  You're going to want to be super careful here, as you could cause all sorts of problems.  

That said, you're probably going to want to make a modification in your fstab, why don't you post /etc/fstab (omitting any personally identifiable stuff please).  And someone will take a look at it.

---

### Post by n.hinton on 2009-11-10
Thanks, I've already modified fstab as I auto mount the partition, see below:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ef051c9e-179a-4158-af23-0332c223a49f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0c9b4203-ebec-4747-a879-3150c279a385 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sda1 /media/disk-1 vfat iocharset=utf8,umask=000 0
/dev/sda1 /media/2D27-07EE vfat iocharset=utf8,umask=000 0

---

### Post by hwttdz on 2009-11-10
edit: Consider this post in combination with what is said below by alphaniner.

So I took out the floppy and wrapped it in code to make it easier to read.  If the mountpoint already exists i.e. /media/disk-1, you should be able to make the changes in fstab (change 2D27... to disk-1).  I've noted that pysdm (a graphical fstab manager) gets hooked on comments, so I don't like to keep comments in my fsab.  Make sure to backup your fstab to your ~.  Also the way to go is uuid, not /dev/... do "ls -l /dev/disk/by-uuid/" to get an idea of what to replace /dev/sda1 with.  Remember _back up_!

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=ef051c9e-179a-4158-af23-0332c223a49f / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=0c9b4203-ebec-4747-a879-3150c279a385 none swap sw 0 0
#/dev/sda1 /media/disk-1 vfat iocharset=utf8,umask=000 0
/dev/sda1 /media/2D27-07EE vfat iocharset=utf8,umask=000 0
```

---

### Post by alphaniner on 2009-11-10
```
#/dev/sda1 /media/disk-1 vfat iocharset=utf8,umask=000 0
/dev/sda1 /media/2D27-07EE vfat iocharset=utf8,umask=000 0
```

I don't know why, but your old entry (1st line) got commented out and replaced (2nd line).  What you want to do is

```
sudo mkdir /media/disk-1
```

then

```
sudo gedit /etc/fstab
```

and change

```
[COLOR="Red"]#[/COLOR]/dev/sda1 /media/disk-1 vfat iocharset=utf8,umask=000 0
/dev/sda1 /media/2D27-07EE vfat iocharset=utf8,umask=000 0
```
to
```
/dev/sda1 /media/disk-1 vfat iocharset=utf8,umask=000 0
[COLOR="Lime"]#[/COLOR]/dev/sda1 /media/2D27-07EE vfat iocharset=utf8,umask=000 0
```

Then reboot.  If everything looks right you can delete folder /media/2D27-07EE (it should be empty!).

Edit: Actually you shouldn't need to reboot.  Just make sure no windows or terminals are accessing /media/2D27-07EE and
```

sudo umount /media/2D27-07EE
sudo mount -a
```

---

### Post by n.hinton on 2009-11-10
Excellent alphaniner that worked 2D27-07EE disappeared and disk-1 was the vfat partition.

I had commented my line:
#/dev/sda1 /media/disk-1 vfat iocharset=utf8,umask=000 0
and added:
/dev/sda1 /media/2D27-07EE vfat iocharset=utf8,umask=000 0
in order to auto mount the partition, because I didn't know the information you just supplied in post 5.

All fixed, many thanks alphaniner

---

