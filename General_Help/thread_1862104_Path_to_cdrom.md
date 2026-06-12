---
title: "Path to cdrom"
date: 2011-10-16
forum: General Help
---

### Post by daniel.cotter on 2011-10-16
I have a laptop with built in dvd burner, and I am using deja-dup to backup /home/me in preparation for upgrading to the latest Ubuntu release  I backed it up successfully to the hard drive, but 1) it looks suspiciously small to be my entire home directory -- is it just compressed that much?  and 2) I copied the contents of the /backup folder (which I created specifically to hold the archive) to a DVD.

I am trying to go through the process of restoring from the backup to ensure it works, but I want to restore it from the DVD I made.  I also want to archive it directly to the DVD when I do it again, so as not to use hard disk space.

My problem is that I cannot find out where the mount point is for the DVD.  fstab only shows the hard drive:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b1cfd664-0167-45c0-804b-cc98b821e265 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4999abfa-969f-4959-b9ab-e9b1fbc57524 none            swap    sw              0       0
```

Can anyone tell me the path to the drive, so i can use it in deja-dup to directly write the backup to dvd and directly restore it from the dvd?

Thanks in advance...

---

### Post by AlphaLexman on 2011-10-16
The command 
```
mount
```
by itself will output all mounted drives.

---

### Post by daniel.cotter on 2011-10-16
Thank you for getting back to me.

I thought about it, and realized that it had been umounted automatically when i finished burning it.  Mounting it again shows it with the mount command, as you said.

Thanks

---

