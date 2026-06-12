---
title: "Can't delete my hard drive..."
date: 2011-09-08
forum: General Help
---

### Post by freeman45 on 2011-09-08
I'm trying to clean the  only HD I have plugged in,  I want everything gone, including ubuntu.  


Problem is i'm unable to delete the volume, it gives me an error message  "the device is busy". I'd be willing to just settle for just reformatting it into "NTFS" so that I can reinstall windows,  but it gives me the same error message  "device is busy". 


When I try to unmount the HD,   but it gives me :

[B]Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda1 from /


[/B]So how do I go about deleting my HD,  should I just place a giant magnet over it? :-x

---

### Post by fdrake on 2011-09-08
you cannot do this when using your ubuntu os . 
use a live cd and do:

```

sudo umount -a
sudo dd if=/dev/zero of=/dev/sda1 # [SIZE="4"][COLOR="Red"]_**BE careful ,this will delete everything!!!**_[/COLOR][/SIZE]

```

can you please post you parttion scheme?
```

sudo fdisk -l

```
so we know the right name of the partitions

---

### Post by CatKiller on 2011-09-08
> **freeman45 said:**
> When I try to unmount the HD,   but it gives me :

```
Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda1 from /
```

Stop trying to format the drive using a program on the drive you're formatting. How could that possibly work?

Use a live cd or something.

---

### Post by Bucky Ball on 2011-09-08
Boot from the LiveCD, 'Try Ubuntu', when at the desktop open Gparted (System>Applications>Gparted or Partition Manager), right click on each partition and make sure they are unmounted. Delete everything, shutdown.

You can't delete the partition the OS is running on so you need to use the CD. Only way you can get all partitions unmounted. ;)

---

### Post by freeman45 on 2011-09-08
oh right, lol
 
 
now you know why i'm switching back to windows, completely illiterate

---

