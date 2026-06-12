---
title: "file ownership questions"
date: 2006-03-05
forum: General Help
---

### Post by ren wins on 2006-03-05
i'm getting kind of annoyed by all of this file ownership junk
i made a folder in my home folder to keep KDE themes in
and i cant move files into it unless i use the terminal and sudo

i think that, when i make folders in konqueror (as opposed to mkdir), they are created as root folders?
it's really kind of annoying, i have a few in my /media/noise directory, so i tried 
```

laserwolf@violet:~$ sudo chown laserwolf /media/noise
chown: changing ownership of `/media/noise': Operation not permitted

```

i'm sure there's a simple solution to the whole thing, i just need a basic course in chown, groups, and ownership.

---

### Post by Xian on 2006-03-05
The /media path does not have user write privileges so even if you change the ownership of a folder in that directory it will still give your access problems. You would be better off to use your home folder for storage of data, files, etc., or a separate partition that is owned by yourself.

As for the theme folder that is giving you problems, I can only think that you did not create it as a user and that would definitely cause some permission issues.

Try this from a terminal:

$ cd /home/<username>
$ mkdir test

Is the folder created and can you move data into it??

---

### Post by ren wins on 2006-03-05
i store all of my media files in 4 huge partitions, and i have them linked to various /media directories in my fstab... do you think i could link them to somewhere in my home folder? 

i can move data into the new folder.  and as a secondary test, i tried making a folder in konquerer (right click > create new > folder) and am able to move stuff into it, which makes me wonder why some folders in my /home directory are root

---

### Post by Xian on 2006-03-05
[QUOTE=ren wins]i store all of my media files in 4 huge partitions, and i have them linked to various /media directories in my fstab... do you think i could link them to somewhere in my home folder? [/quote]

Oh, that's different. You should be able to set up write access to those.
What does your fstab look like?

[QUOTE=ren wins]i can move data into the new folder.  and as a secondary test, i tried making a folder in konquerer (right click > create new > folder) and am able to move stuff into it, which makes me wonder why some folders in my /home directory are root[/QUOTE]

Only method I know of is you were an admin when it happened.

---

### Post by ren wins on 2006-03-05
fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 	/media/windows 	ntfs 	umask=0222 	0 	0
/dev/hdb6 	/media/noise 	vfat 	umask=000 	0 	0
/dev/hdb7 	/media/eyes 	vfat	umask=000 	0 	0
/dev/hdb8	/media/support	vfat	umask=000	0	0
/dev/hdb9	/media/static	vfat	umask=000	0	0

```

---

### Post by Xian on 2006-03-05
Try this:

```
/dev/hdb6 /media/noise vfat umask=0000 0 0
```

---

