---
title: "Can't copy files to new volume"
date: 2010-02-24
forum: General Help
---

### Post by d3v1150m471c on 2010-02-24
Why can I not drag and drop files to the new volume in dolphin? I tried doing it as root and it basically told me the same thing, that I cannot write in this volume...

---

### Post by d3v1150m471c on 2010-02-24
It won't let me change the permissions either

---

### Post by bodhi.zazen on 2010-02-24
More information please.

Try from the command line, 

ls -la /mount/point

cp foo /mount/point/foo

error messages ?

file system type ????

---

### Post by d3v1150m471c on 2010-02-24
Basically all I have is read access.
```

d3v11@d3v11m4ch1n3:/media$ sudo chmod 755 'New Volume'
chmod: changing permissions of `New Volume': Read-only file system

```

---

### Post by d3v1150m471c on 2010-02-24
I don't need any of the information currently on it so I could just reformat it. I can copy files from it fine
but I cannot add anything to it. It's incredibly annoying.

---

### Post by d3v1150m471c on 2010-02-24
fdisk doesn't work, mkfs -T vfat doesn't work, chmod doesn't work, kdesudo dolpin doesn't work... I'm close to smashing it open with a hammer and writing the names of my files in sharpie on it's components but I haven't gotten that far yet.

---

### Post by bodhi.zazen on 2010-02-24
You can not chown or chmod FAT or NTFS permissions. Permissions are set at the time you mount the volume.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Without additional information it is hard to help you.

What kind of partition ? internal or external ? What file system ? How did you mount it ? from the GUI or command line ?

Is the device working ? you could always have a corrupt file system.

---

### Post by d3v1150m471c on 2010-02-24
The device works, It's an external hard drive connected via usb, kubuntu mounts it by default when it's initially plugged in, and I've failed to write to it with both command and gui. I just use it for storage. I dunno what filing system it is. I bought it and slapped information on it.

EDIT: FAT32

To add to this nuisance it won't let me "umount" it either :-). *polishes the hammer*

---

### Post by d3v1150m471c on 2010-02-24
Problem solved...without smashing it even :).
```

mkfs.ext3 /dev/sdc

```

I had to play around with it for a while...The first few times I tried that it kept telling me it was in use. I wonder what caused this?

---

