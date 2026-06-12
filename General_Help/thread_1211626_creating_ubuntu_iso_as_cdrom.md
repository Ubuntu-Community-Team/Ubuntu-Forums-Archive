---
title: "creating ubuntu iso as cdrom"
date: 2009-07-12
forum: General Help
---

### Post by gerbilburp on 2009-07-12
hello

i need to grab a file from the ubuntu iso but unfortunately i do not have the physical cd

is it possible to replace the cd-rom and mount the ubuntu iso

ive mounted the iso but only able to create it as cdrom0 but its more of a folder then a cd and is very difficult to download from from it (beginner)

thanks in advance!!!

---

### Post by blueridgedog on 2009-07-12
You can mount an iso image:

```
mount -o loop /path/to/and/nameofisofile.iso /mnt/nameofdirectory
```

Just make certain that the mount point exists.

---

### Post by gerbilburp on 2009-07-12
will that replace the cd-rom?

i only know how to get files from the cd-rom but since i do not have the cd (only the iso)

what do you mean by directory?

---

### Post by Rocket2DMn on 2009-07-12
In Ubuntu (and all linux distros) when you mount a partition/hard drive/cd it is a directory on the filesystem, not a drive letter like in Windows.  Typically we mount these at /media/something or /mnt/something.  This is usually done automatically when you plug in a drive, or insert a cd.  A cd defaults to the /media/cdrom directory.

So, what you need to do is create the mount point (directory), then run the mount command:
```
sudo mkdir /media/ubuntu_iso
sudo mount -t isso9660 */path/to/iso/file* /media/ubuntu_iso
```

Then you can access the "cd-rom" files from /media/ubuntu_iso.

When you are finished, you should unmount the image:
```
sudo umount /media/ubuntu_iso
```

---

