---
title: "Check Spelling Error !"
date: 2011-04-08
forum: General Help
---

### Post by etdsbastar on 2011-04-08
Please help, I am getting the following message on startup:

Could not find /media/...??
Please check spelling and try again.

---

### Post by sanguinoso on 2011-04-08
The only reasons I can think of:

1) Is that line in your /etc/fstab ?

2) Did you install something from that place that didn't copy over to your main file system?

---

### Post by etdsbastar on 2011-04-08
no no such line indicating that folder in fstab.

What does the second point means?

---

### Post by harun3d on 2012-04-23
[FONT=monospace]1)Writing:[/FONT]
```
 gksu gedit /etc/fstab
```gave
[PHP]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=....... /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=......    none            swap    sw              0       0
[/PHP]so my missing file "/media/4GBVK/rz" is not present here.


2)Yes. Conduit (ubuntu synchronization program) synchronizes my usb  stick  with my documents. and when the usb stick is missing he shows this   message.  But Conduit does not start at startup also not in the   background.  

3)      Code:
     sudo apt-get install gvfs-backends 
 did not fix it

4) Probably I have to reinstall gvfs-backends, nautilus, ubuntu-desktop and some other stuff as it is written here:  [http://ubuntuforums.org/showthread.php?t=1278395](http://ubuntuforums.org/showthread.php?t=1278395)
But it is not written how.

5)"libgnomevfs2-extra" is probably not the solution as written in another page on this forum

6) installing smbfs would probably not fix it.

7) The missing file is not any more in my favorite files list in the sidebar of the file explorer

---

