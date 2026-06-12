---
title: "Format bricked USB stick"
date: 2011-05-15
forum: General Help
---

### Post by sid.mallya on 2011-05-15
Hey guys ! 

I was formatting the USB stick on Linux and due to some error, the computer restarted. Now, while the bigger problem is what error made the computer restart, I am currently faced with a much more immediate problem.

My USB stick is bricked and is pretty much not getting mounted at all ! I can view the partition if I try

```
fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1011      986705+   c  W95 FAT32 (LBA)

```

in the terminal .. But if I try

```
sudo mount /dev/sdb1 /media/sdb1

mount: mount point /mount/sdb1 does not exist

```I get an error saying, mount point does not exist.

---

### Post by sid.mallya on 2011-05-15
(The boot flag is up because it is a liveUSB stick for Ubuntu 11.04)

---

### Post by sid.mallya on 2011-05-15
Okay .. So the problem still persists. I tried running it on a Windows machine and apparently, the drive is "read-only" and cannot be accessed; no idea what that means. But in a nutshell, I cannot format it on a Win machine either. The drive does show up in "My Computer" though, just with no information at all.

---

### Post by NightwishFan on 2011-05-15
You could have used the gnome disk utility or gparted to format it.

---

### Post by dandnsmith on 2011-05-15
> sudo mount /dev/sdb1 /media/sdb1

mount: mount point /mount/sdb1 does not exist

There's an inconsistency in these messages!
What it seems to be saying (ignoring the inconsistency) isn't that the filesystem isn't there, just that the mount point isn't.

Can you recheck that the mount point you are trying to use really does exist?

---

### Post by sid.mallya on 2011-05-15
Hmm .. Well ya, using Disk Management (on Windows) or GParted does solve the problem. Thank you fellas !

---

