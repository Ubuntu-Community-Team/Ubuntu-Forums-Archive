---
title: "Accessing data on image made from dd"
date: 2010-07-15
forum: General Help
---

### Post by protargol on 2010-07-15
So I backed up my windows hard drive using dd and turned it into one huge image file.  I didn't realize this beforehand, but this image is not an ISO equivalent type.  However, it would be nice if I could access everything on the image just by mounting it instead of having to transfer it back to /dev/sda or something.  Any tips on how this can be done, or a better way I can back up everything?

---

### Post by lykwydchykyn on 2010-07-16
Have you tried:
```

sudo mount myimagefile.img somefolder/ -o loop

```

---

### Post by protargol on 2010-07-16
It kicks back?
```
mount: you must specify the filesystem type
```

Should I dig through the mount man page?

---

### Post by prodigy_ on 2010-07-16
Try the same with **-t ntfs** option added.

---

### Post by renkinjutsu on 2010-07-16
The problem is that he copied the whole device into a single file instead of copying the individual partitions into different files. So he now has one huge file that contains the MBR/bootloader and all that good stuff, so he's not able to mount it like a regular image of a filesystem.


.. if you know the exact size of the partitions and stuff you can try to dd the partitions OUT of that file into its own file.. but that is a very precise procedure, and i doubt you have the exact partition sizes (down to the bytes) written down somewhere

---

### Post by dcstar on 2010-07-16
> **protargol said:**
> So I backed up my windows hard drive using dd and turned it into one huge image file.  I didn't realize this beforehand, but this image is not an ISO equivalent type.  However, it would be nice if I could access everything on the image just by mounting it instead of having to transfer it back to /dev/sda or something.  Any tips on how this can be done, or a better way I can back up everything?

[http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux](http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux)

---

