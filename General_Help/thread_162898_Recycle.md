---
title: "Recycle?"
date: 2006-04-19
forum: General Help
---

### Post by kyoushu on 2006-04-19
I just installed Ubuntu on my new laptop and it's running great.  I'm currently having a few problems, but one which I wish to address now is the fact that the Recycle Bin is gone.  Propably I accidently deleted it off the bottom bar thing.  Anyway I can get that back?

Also, My Windows XP PRO Partition, which came with laptop is NTFS and none of the drives can be read by Ubuntu(can't open C:\ drive to edit files, etc).  I'm pretty sure that because it's NTFS Gnome can't read it.  Just checking, and is there anyway I can fix it?

---

### Post by lucia_engel on 2006-04-19
Recycle Bin:
You can right click on the bottom bar and choose "Add to Panel", Scroll down until midway and you'll see the Trash bin applet, click Add.

I'll leave the NTFS question for the experts to explain

---

### Post by Nequeo on 2006-04-19
[QUOTE=lucia_engel]Recycle Bin:
You can right click on the bottom bar and choose "Add to Panel", Scroll down until midway and you'll see the Trash bin applet, click Add.

I'll leave the NTFS question for the experts to explain[/QUOTE]

Linux can read NTFS, but write support is experimental and definately not reccomended. 

During the installation Ubuntu ought to have detected and mounted your NTFS partitions as 'read only' automatically. If it hasn't done this, could you please go to 'System--->Administration--->Disks', and tell us what your drives/partitions and their respective file-systems are? This will help us give you customized instructions.

You might also just want to try searching [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) for NTFS, that will probably answer all your questions, too.

Cheers,

---

### Post by Qrk on 2006-04-19
Writing to ntfs is not supported on linux, but you can read ntfs. So you cannot edit files on your ntfs partitions. Currently you can read your ntfs partitions but only as root (use *gksudo nautilus* to get to a root file browser) To allow a normal user to view the ntfs drive change fstab:

```
sudo gedit /etc/fstab
```

Find the line that looks something like this, it may have a different mount point:

```
/dev/hda1       /media/hda1     ntfs    defaults       0       0
```

and change the "defaults" part so that it looks like this:

```
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222       0       0
```

The do:
```
sudo umount -a
sudo mount -a
```

If you don't have a line corresponding to your windows partition, just copy that line  (2nd one)to the end of /etc/fstab. 

Then do:
```
sudo mkdir /media/hda1
sudo mount -a
```

---

### Post by kyoushu on 2006-04-19
Thanks all three of you.  Ill get back and see what works after I finish some homework. :D

---

