---
title: "The magical moving USB drive"
date: 2009-10-13
forum: General Help
---

### Post by fowie on 2009-10-13
I bought an external USB drive for nightly backups.  I'm using rsnapshot for my backups, so they happen very regularly.  I plugged in the drive and did an 
```

ls /dev/disk/by-uuid

```
which gave me the UUID of the USB drive.  I added it to my fstab like so:
```

UUID=82cf91ff-7908-4725-8a08-f60c347af81e	/fsbackup	ext3	relatime,defaults	0	3

```
However, after so long (I'm not sure how long) if I try 
```

cd /fsbackup
ls

```
I get an Input/Output error.  I thought it was a problem with the drive, but the real reason is that the drive letter has changed?  For instance, I boot up the computer for the first time, and the USB drive is /dev/sdb1, and df -h shows that /dev/sdb1 is mounted to /fsbackup.  I get the i/o error, and to remedy it I try:
```

sudo mount -a

```
and I can access the files again, now if I do df -h, it shows that not only is /dev/sdb1 mounted to /fsbackup, but so is /dev/sdc1.  What is causing the USB drive to change letters, and why is mounting by UUID working, but not staying permanent?  Why is the drive disconnecting and coming back as a new letter?  How can I permanently mount the USB drive?  The computer it is plugged into is being used as a server, so rebooting frequently is something I'd like to avoid.

---

