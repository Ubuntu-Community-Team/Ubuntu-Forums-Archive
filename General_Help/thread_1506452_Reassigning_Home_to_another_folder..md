---
title: "Reassigning Home to another folder."
date: 2010-06-10
forum: General Help
---

### Post by grindboy on 2010-06-10
Hi Guys,

I've just decided (as you do!) to rearrange all my OSes. I now have Ubuntu and Windows 7 on one hard drive and all my data on another hard drive formatted as FAT32 so that both OSes can read it.

I've seen plenty of tutorials on how to move your home directory to another hard drive but I just want the contents of the DATA drive to become my Home directory.

Is this possible thanks

Grindboy

---

### Post by ThesaurusRex on 2010-06-10
Should be, using mount.

```
man mount
```

---

### Post by srs5694 on 2010-06-10
It's not possible, or at best, it's likely to cause problems. The reason is that FAT doesn't support Linux filesystem features, such as ownership, permissions, symbolic links, and so on, and some programs expect to be able to use these features in users home directories.

That said, you can mount your shared-data directory as a subdirectory of /home or of your home directory (/home/grindboy or whatever you use). To do so, you must first create an empty directory to use as the mount point and then edit /etc/fstab to permanently mount the FAT partition at that location, using whatever options are necessary to set permissions, ownership, and other filesystem features on the partition.

---

### Post by grindboy on 2010-06-10
OK I'll try that thanks srs5694

[edit]
OK I'm having difficulty adding it to FStab. This is the string I'm using:
```
UUID=6732-CECC	/home/michael/Data Fat 	defaults 	    0	    0
```

But when I reboot it tells me that there was an error mounting /home/michael/Data.

What is it I'm doing wrong?

[edit2] **Fixed now. Turns out you need to label the drive as VFAT not FAT if it is formatted as FAT32 Thanks for the help guys**

[edit3] OK so for anyone coming across this in the future and trying to solve the same problem my final FSTAB entry looks like this:

```
/dev/disk/by-uuid/6732-CECC	/home/michael/Data vfat 	users,umask=0000	    0	    0
```

The /dev/disk/by-uuid/ bit is a work around for a known Gnome bug which can cause hard drives to show up twice in nautilus. The users and umask=0000 bit mounts the drive as the user rather than root. I'm unsure if both as necessary but this works for me.

---

