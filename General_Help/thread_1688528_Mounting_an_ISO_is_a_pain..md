---
title: "Mounting an ISO is a pain."
date: 2011-02-15
forum: General Help
---

### Post by PoopLoops on 2011-02-15
I have something I want to install that's on an ISO file. How the hell do I do that in Ubuntu? Let me explain, this is what I've tried so far:

Downloaded fuseiso. Mounted ISO with "fuseiso <iso file> <mount point>". I cd to the mount point in a terminal. Can't run ./install because permission is denied. Can't do "sudo ./install" because that isn't recognized. I then enter "sudo su" and try ./install. No dice, still bad permissions.

I unmount the ISO, then try "sudo fuseiso <iso file> <mount point>" and it gets even worse because then the permissions are all set to "?" instead of an actual user and group.

I have admin rights on this machine and have made myself part of the fuse user group. What the hell do I do?

---

### Post by marshmallow1304 on 2011-02-15
I'm not familiar with fuseiso. Try loop mounting it.

As root or with sudo:
```
mount -o loop image.iso /mount/point
```


Also, the install might not be executable.  Try
```
sh install
```

---

### Post by PaulReaver on 2011-02-15
sudo su
mkdir /mnt/iso
mount -o loop image.iso /mnt/iso
exit


to unmount you'll need to use sudo again
sudo umount /mnt/iso

---

### Post by PoopLoops on 2011-02-15
That worked! Many thanks. :)

---

### Post by c0moshack on 2011-02-16
I use the scripts that were mentioned in the following link to mount/unmount .iso's: 
 
    [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)
 
It works pretty well and is easy to use once the scripts are in place.

---

