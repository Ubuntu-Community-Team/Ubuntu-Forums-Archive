---
title: "Can't Mount External HDD"
date: 2009-09-16
forum: General Help
---

### Post by raywood on 2009-09-16
Hi, all.  I'm using Ubuntu 9.04 x64.  Trying to copy files to an external 3.5" NTFS hard drive via USB or eSATA (external enclosure accommodates both); getting same results either way.  Have previously accessed drive on this machine at /media/OFFSITE.  (Prefer /media to /mnt because I have other partitions there too.)  Windows on a different machine sees and uses the drive, no problem.  Clean shutdown.  CHKDSK /R run twice; no further errors.

Problem:  sudo mount -a yields this:

```
fuse: failed to access mountpoint /media/OFFSITE: No such file or directory.
```

However, when I mkdir /media/OFFSITE and then run an rsync to OFFSITE, the files are not copied to the external drive.  Instead, I get copies in a folder on the source drive named /media/OFFSITE.

Soooo ... how do I get the external drive to be accessible (again) at /media/OFFSITE?

Thanks!

---

### Post by ajgreeny on 2009-09-16
Do you have the disk labelled with a name that is different to OFFSITE as it is possible that the disk is automounting to another /media folder with the disk's label as its name.  If that is the case, you will not be able to mount it to OFFSITE as well.

---

### Post by raywood on 2009-09-16
Ubuntu seems to recognize the external drive as having the name OFFSITE.  For instance, right now it is showing up in Nautilus (not as root).  It doesn't always show up there, but for some reason it is now.  It's shown with the little red USB symbol.  When I double-click on it there, I get "Cannot mount volume.  You are not privileged to mount the volume 'OFFSITE'."  Then, after a minute, I get another error:  "Unable to mount location.  DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply."  But I don't really understand why it's showing up there, because when I navigate to /media in Nautilus as root, I don't see it.  

Ah.  But then, continuing the exercise, I create /media/OFFSITE in Nautilus as root.  This yields no joy:  "sudo fdisk -l" shows the external drive as /dev/sdd5, but it doesn't show up in df -h.  But then -- what's this? -- "sudo mount -a" does the trick ( /etc/fstab has a line reading "/dev/sdd5 /media/OFFSITE ntfs-3g defaults,force 0 0"). I'm back in business!

Thanks for the nudge in the right direction!

---

### Post by ajgreeny on 2009-09-17
Why do you have the force option in the fstab line, and perhaps more importantly, why bother with a line in fstab at all?  A usb attached drive should mount automatically without any fstab input requirement, and if you have disk labelled the drive, it should auto-mount to a folder in /media with that label name.

---

