---
title: "floppy no media found"
date: 2009-10-07
forum: General Help
---

### Post by rtalcott on 2009-10-07
fstab line is:
/dev/fd0  /media/floppy0  auto  rw,user,noauto,exec,utf8    0  0 

The machine will boot from the floppy (DOS) BUT if I boot Ubuntu and then try to get to the disk I am told that there is no media in the drive...and I have this happening on 3 machines...3 different floppy drives

What am I missing?

Thank you.
rt

---

### Post by khelben1979 on 2009-10-07
You have the option to manually mount the drive. You can try:
```

sudo mount -t vfat /dev/fd0 /media/fd0
``` and ```
man mount
``` for information on how to use the mount command.

---

### Post by rtalcott on 2009-10-07
Thank you!

That works!
rt

---

### Post by khelben1979 on 2009-10-07
Glad that you got it working!

---

### Post by rtalcott on 2009-10-07
But now:
sudo mount -t vfat /dev/fd0 /media/floppy0
[sudo] password for rtalcott: 
mount: /dev/fd0: can't read superblock

It WAS working...but **I** must have done something to make it NOT work...

fstab is now:
/dev/fd0 /media/floppy0 auto noauto,user,exec,rw,sync 0 0

The only thing I need the floppy for is to upgrade the BIOS...I've had no luck making a DOS bootable (FREEDOS) usb..
rt

---

