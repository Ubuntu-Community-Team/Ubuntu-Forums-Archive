---
title: "settings didn't stick after reboot"
date: 2006-04-13
forum: General Help
---

### Post by Gaia on 2006-04-13
hi,

I used umount and mount to gain access to my other drives and it was all working well, i changed the icons to make it look nice ;) and all that...when i restarted and loaded Ubuntu back up, the changes were gone? 

Is there something special i have to do to make the changes stay?

Thanks.

---

### Post by taurus on 2006-04-13
If you mount your drive by hand, then you have to do that everytime you boot Ubuntu!  If you want it to be permanent, then you need to edit your /etc/fstab!  Tell me what partition you want to mount, filesystem of that partition, and where you want to mount it.  Then, I will show you exactly how you would add an entry to your /etc/fstab...  ;)

---

### Post by Gaia on 2006-04-13
thanks!

My hard drive is hdb5, it's NTFS, and i want to mount it to my home folder in a directory called downloads.

And my second one is hda1, also NTFS (this one holds WindowsXP) and i think i want to unmount that one alltogether so that it doesn't show up on my Ubuntu desktop.

---

### Post by taurus on 2006-04-13
[QUOTE=Gaia]thanks!

My hard drive is hdb5, it's NTFS, and i want to mount it to my home folder in a directory called downloads.

And my second one is hda1, also NTFS (this one holds WindowsXP) and i think i want to unmount that one alltogether so that it doesn't show up on my Ubuntu desktop.[/QUOTE]
Do you know that you can only read from NTFS, NOT write to it so I don't see any reason why you want to mount /dev/hdb5 to your home directory?  Just mount it somewhere else and you can still have access, read, to it!  Open a terminal by clikcing Applications -> Accessories -> Terminal.  Then type
```

sudo mkdir /windows <-- to create a mount point...
sudo cp /etc/fstab /etc/fstab.bak <-- make a backup copy just in case...
sudo gedit /etc/fstab <-- edit /etc/fstab...

```
Now add the following line to the end of it and save it.
```

/dev/hdb5  /windows  ntfs  defaults,umask=0222  0  0

```
Then, mount it with
```

sudo mount -a
df -h

```
You now should see your /dev/hdb5 in /windows from the last command...

---

### Post by Gaia on 2006-04-13
hi thanks, well all i need to do anyway is read not write.

So, does this look good? I use umount to unmount hda1 and unmounted hdb5 and re-mounted it. 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb5       /windls         ntfs    defaults,umask=0222  0  0

```

I just removed hda1 all together, would that cause a problem or is there some other way to permently unmount it?

Thanks.

---

### Post by taurus on 2006-04-13
If you don't want a partition to mount, then remove it from /etc/fstab yes, it is safe to unmount it and remove the entry for /dev/hda1 from /etc/fstab.  Your /etc/fstab looks good to me.  Just reboot and everything should be fine.

---

