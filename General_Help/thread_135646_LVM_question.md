---
title: "LVM question"
date: 2006-02-24
forum: General Help
---

### Post by yanik on 2006-02-24
Hi 

I have this new server I have to take care of, there is a LVM consisting of 3 300GB hard disks.  Two internal and one in a drawer.  This is silly, the whole purpose of the drawer is lost with this setup.  I want to take the disk in the drawer out of the LVM.  I know how to do that, but my question is how do I know which disk to take out.  

I have those 3 hard disks:

/dev/hda4
/dev/hdb
/dev/hde

I would assume it's the last one, /dev/hde, but how can I make sure?

Thanks

Yanik

---

### Post by jimcooncat on 2006-02-24
kinda low tech, but if it's got a blinking light on it do a huge read from the drive (dd maybe?), you can pump it to /dev/null. If the light burns bright and your other disks aren't grinding, I'd say you found it.

---

### Post by yanik on 2006-02-24
I can't do that jimcooncat.

It's a logical volume, not a physical volume, the system sees the 3 disks as one.  

See the output of mount:

```
/dev/mapper/volg-backlv on /backups type ext3 (rw)
```

---

### Post by lamego on 2006-02-24
Please note that I am only familiar with LVM from comercial unixes.
To remove  a disk from a VG you first chould  check if the physical disk is in use (on the LVM I know the disks in use would be shown by vgdisplay -v volume_group.
If there is data on the disk you want to remove you must force the data to be moved to some other space (whatever is free on the other physical disks), this would be done with the pvmove command.
I don't know how this commands map into the linux LVM, never used it...

---

### Post by jimcooncat on 2006-02-26
Typing **lvm** into the command line will display lvm commands. You can then enter **lvm help *command*** to get a arguments list, or **man *command*** to read that particular command's man page if one's available. You will probably have use **sudo lvm *command*** to actually invoke a command, as most of these need root access.

Here is output for the **lvm** command, edited for brevity, leaving the one which might be most helpful:

  vgreduce        Remove physical volume(s) from a volume group

---

