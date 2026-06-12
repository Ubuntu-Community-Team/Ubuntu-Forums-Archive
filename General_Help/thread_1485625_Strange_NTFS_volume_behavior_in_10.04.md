---
title: "Strange NTFS volume behavior in 10.04"
date: 2010-05-17
forum: General Help
---

### Post by Alex Farber on 2010-05-17
Ubuntu 64 bit is installed on the hard disk with two partitions: one for Ubuntu, another is NTFS partition called Shared. Before upgrading to 10.04 Shared volume was available. To mount it, it was necessary to enter the password.
After upgrading to 10.04, I see two volumes: Shared and Shared_. Places menu contains Shared item. When I click it, it opens without password, and shows /media/Shared_, with correct contents. Original Shared volume appears in the media directory:

```

root@alex-64:/media# ls -l
total 12
lrwxrwxrwx 1 root root    6 2010-04-21 19:49 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-04-21 19:49 cdrom0
drwx------ 2 root root 4096 2010-05-09 08:25 Shared
drwx------ 1 alex alex 4096 2010-05-17 08:56 Shared_

```

Shared volume is empty. Can this be fixed? It is OK to work with Shared_ volume?

---

### Post by sedawk on 2010-05-17
If a directory /media/drivename exists when mounting
"drivename" the fallback method is to use
"/media/drivename_" as mount directory

Most likely /media/shared is a leftover from a unclean
unmount in the past.

I recommend to first unmount the shared partition.
The directory /media/shared_ should be gone now
and /media/shared should be an empty directory
so you can savely remove it with "sudo rmdir /media/shared".

If you now connect the drive it should use /media/shared
again.

---

### Post by DawieS on 2010-05-17
[FONT=monospace]Also, if you want the password behavior as before, open a terminal and enter:

[/FONT]```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```[FONT=monospace]

Change the first occurrence of '**ResultActive=yes**' to '**ResultActive=auth_admin_keep**' and save. The behavior should now revert to the default of requiring a password when mounting internal disks/partitions.
[/FONT]:smile:

---

### Post by Alex Farber on 2010-05-17
Thank you, got it working.

---

