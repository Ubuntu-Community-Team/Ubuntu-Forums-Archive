---
title: "Directories’ permisions for automounted usb hard drive in Ubuntu 9.10"
date: 2009-12-25
forum: General Help
---

### Post by trancer_ on 2009-12-25
Hello.
  

I've noticed that directories' permissions for my automounted USB hard drive formatted in NTFS in Ubuntu 9.10 are 700. This is inconvenient for me. On Ubuntu 8.04 LTS it was 777 everywhere and it was good. Where can I change those default automount permissions for such a drive?


  Thank you.

---

### Post by SuperSonic4 on 2009-12-25
Automounted as in fstab?

If so post out the relevant line in /etc/fstab

If not couldn't you run a chown or chmod on the directory? Caution - this may not be safe as I'm guessing

---

### Post by Mahngiel on 2009-12-25
here's my fstab. it let's you automount and have permissions

```

/dev/sda2                                  /media/Storage  vfat         auto,utf8,umask=007,uid=1000,gid=46   0  0  

```

---

### Post by trancer_ on 2009-12-25
Here's my /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ed594b1f-7648-4cad-9571-f70454304b9a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=671c7475-348c-4c7a-94d2-82096f1efb8c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

But I believe this is done not by means of fstab.
Also CHMOD does not change rights on NTFS files from mounted usb hard drive.

---

### Post by Mahngiel on 2009-12-25
edit your fstab via

"sudo gedit /etc/fstab"

and amend the options

```

 devgid=46,devmode=664 0 0

```to include
```

auto,utf8,umask=007,uid=1000

```

---

### Post by Mahngiel on 2009-12-25
also, see bodhi.'s [Howto Fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by trancer_ on 2009-12-25
Adding options did not help. Still directories' permissions are 700

Here's /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ed594b1f-7648-4cad-9571-f70454304b9a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=671c7475-348c-4c7a-94d2-82096f1efb8c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664,auto,utf8,umask=007,uid=1000 0 0
```

---

