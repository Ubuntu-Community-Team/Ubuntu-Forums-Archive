---
title: "Virtually mounting .ISO files?"
date: 2009-10-07
forum: General Help
---

### Post by ErikEhlert on 2009-10-07
The titles pretty much explains it, I am running Ubuntu 9.04, and I need some program that will allow me to virtually mount an ISO file. Since I don't have a DVD drive, just a pathetic little CD drive I had since the Windows 2000 days :P, this isn't for mounting Distros, its for ISO files much larger than a standard 700MB disk..

---

### Post by jbrown96 on 2009-10-07
So you have a DVD iso on your hard drive that you need to mount as a drive?

1) create the folder where you want to mount it. Personally, I like to mount drives in my home folder because it eliminates some permission issues. However, Ubuntu defaults to the /media folder when automounting drives. It's up to you. I'm going to write this assuming you use your home directory
```
mkdir Desktop/mount
``` you can put this somewhere else (besides the desktop) and rename mount to something else, just remember to alter the commands below if you do.
2) mount the iso
```
sudo mount /path/to/iso Desktop/mount -o loop
```
The /path/to/iso part is the iso location. For example, I have a XBMC Linux iso, and here's the command I would use
> sudo mount /home/justin/DesktopXBMC_Live.iso Desktop/mount -o loop
The disk will now be accessible in Desktop/mount.

If you are trying to watch a DVD, you can actually just open the iso in VLC. 

To unmount it, ```
sudo umount Desktop/mount
``` notice that it's umount and not unmount.
This won't copy the iso image anywhere, so the size of the iso doesn't matter. That command will work for CD, DVD, and Blu-ray isos.

---

### Post by Azuu on 2009-10-07
Just ISO files or anything else in general that is mountable? There are some bash commands and scripts that would work out fine, but you are probably looking for a GUI mounter.

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)
Acetone iso should be in synaptic package manager and mounts most disk formats.

---

### Post by Diabolis on 2009-10-07
```
sudo apt-get install gmountiso
```

---

### Post by shaggy999 on 2009-10-07
I've noticed that if I simply double-click an iso on my desktop in jaunty the default behavior is to automount the iso image.

---

### Post by geirha on 2009-10-08
> **shaggy999 said:**
> I've noticed that if I simply double-click an iso on my desktop in jaunty the default behavior is to automount the iso image.

The default behavior when double-clicking an .iso-file is to open it with file-roller, the default archiver in Ubuntu. It just opens it like it would a .zip, .tar.gz or .rar file, allowing you to browse the files and extract some or all of them. This is not the same as mounting, but if you only need to copy files from it, it's the easiest option.

---

### Post by shaggy999 on 2009-10-09
> **geirha said:**
> The default behavior when double-clicking an .iso-file is to open it with file-roller, the default archiver in Ubuntu. It just opens it like it would a .zip, .tar.gz or .rar file, allowing you to browse the files and extract some or all of them. This is not the same as mounting, but if you only need to copy files from it, it's the easiest option.

No, it is not being opened with file roller. It was mounted to a folder in my /media directory and an icon was placed on my desktop. A window then opens up displaying the root directory of the iso. After closing the window the file is still mounted with an icon on my desktop. I have to right-click the icon on my desktop and check "unmount".

---

### Post by theozzlives on 2009-10-09
> **shaggy999 said:**
> No, it is not being opened with file roller. It was mounted to a folder in my /media directory and an icon was placed on my desktop. A window then opens up displaying the root directory of the iso. After closing the window the file is still mounted with an icon on my desktop. I have to right-click the icon on my desktop and check "unmount".

Funny, my default behavior has always been to burn the .iso

---

### Post by geirha on 2009-10-10
> **shaggy999 said:**
> No, it is not being opened with file roller. It was mounted to a folder in my /media directory and an icon was placed on my desktop. A window then opens up displaying the root directory of the iso. After closing the window the file is still mounted with an icon on my desktop. I have to right-click the icon on my desktop and check "unmount".

On my system the default is to open with file-roller, but I do see the option "Open with Archive Mounter" in the right-click menu, which does indeed do what you describe. Never noticed that before. Very handy :)

---

### Post by slakkie on 2009-10-10
```

#!/bin/bash

for i in $@ ; do
    dir=$(basename $i .iso)
    sudo mkdir -p /mnt/$dir
    sudo mount -o loop $i /mnt/$dir
done

```

To unmount you can use this:

```

#!/bin/bash

for i in $@ ; do
    dir=$(basename $i .iso)
    sudo umount /mnt/$dir
    sudo rmdir /mnt/$dir
done

```

Name the script, make them executable and run them

```

mount_iso /path/to/some.iso
umount_iso /path/to/some.iso

```

---

### Post by geirha on 2009-10-10
@slakkie. And what if the file has spaces in it? or glob characters?

---

### Post by marmotapl on 2009-10-10
> **diabolis said:**
> ```
sudo apt-get install gmountiso
```

x2

---

### Post by slakkie on 2009-10-10
> **geirha said:**
> @slakkie. And what if the file has spaces in it? or glob characters?

Then you need to adjust the script or the filename.

---

### Post by Yannick Le Saint kyncani on 2009-10-10
> **Diabolis said:**
> ```
sudo apt-get install gmountiso
```

+1, gmountiso is a graphical interface to mount/umount iso files.

---

