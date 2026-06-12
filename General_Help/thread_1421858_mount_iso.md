---
title: "mount iso"
date: 2010-03-04
forum: General Help
---

### Post by frito on 2010-03-04
hi there i am having issues installing a program i have on an iso (its for linux)

i need to run the install script in the iso.
I can mount it using whatever the mounting program is but then I cant find the mount point to run **install**

if i try to mount it myself,
using:
[B]mkdir -p /mnt/here
mount -o loop /path-to-iso/x.iso /mnt/here
[/B]
it says cannot find **/path to iso/x.iso** in **etc/fstab**

what do i do?

---

### Post by Chris Musampa on 2010-03-04
I think you have to use sudo to mount it if theres no fstab entry.

---

### Post by frito on 2010-03-04
i was using sudo... i forgot to write it..sorry

---

### Post by gmargo on 2010-03-04
You probably need to add an option to mount: "**-t iso9660**".  This is the file system type, which is probably the info it was seeking in /etc/fstab.

---

### Post by sandyd on 2010-03-04
you can try mounting it with acetoneiso.
its a nice gui program for mounting isos.
you can download it.... - after getdeb is up again.

---

