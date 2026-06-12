---
title: "simulate a floppy drive with user read write"
date: 2010-09-17
forum: General Help
---

### Post by eddarl on 2010-09-17
I have a computer with no floppy drive (x64 ubuntu lucid installed)
I have a program (wine windows xp) that will only save data and export data from/to a floppy drive.

I found information on setting up an emulated floppy drive.

i.e. sudo dd bs=512 count=2880 if=/dev/zero of=imagefile.img
     sudo mkfs.msdos imagefile.img
     sudo mount imagefile.img /media/floppy -o loop

I modified the winecfg to include under the drive section A: /media/floppy.

Problem is I cannot write to the drive as a normal user.
I have tried everything I know but only root can read write to the drive.

Is there someway to set up this emulated floppy to allow me as a user to write and read contents.

Thank you

---

### Post by dcstar on 2010-09-18
> **eddarl said:**
> 
..........
Problem is I cannot write to the drive as a normal user.
I have tried everything I know but only root can read write to the drive.

Is there someway to set up this emulated floppy to allow me as a user to write and read contents.

Thank you
Set the permissions on the mount point correctly, and
```
man mount | grep users
```

---

