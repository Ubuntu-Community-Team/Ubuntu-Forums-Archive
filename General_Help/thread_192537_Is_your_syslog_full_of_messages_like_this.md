---
title: "Is your syslog full of messages like this?"
date: 2006-06-08
forum: General Help
---

### Post by mannheim on 2006-06-08
I have two dapper installations, (work and home). In both cases, the syslog is getting filled up with this:

```

Jun  8 21:43:50 localhost kernel: [4659909.364000] VFS: busy inodes on changed media.
Jun  8 21:43:50 localhost kernel: [4659909.805000] VFS: busy inodes on changed media.
Jun  8 21:43:52 localhost kernel: [4659911.422000] VFS: busy inodes on changed media.
Jun  8 21:43:52 localhost kernel: [4659911.428000] VFS: busy inodes on changed media.
Jun  8 21:43:52 localhost kernel: [4659911.814000] VFS: busy inodes on changed media.
Jun  8 21:43:52 localhost kernel: [4659911.820000] VFS: busy inodes on changed media.
Jun  8 21:43:54 localhost kernel: [4659913.439000] VFS: busy inodes on changed media.
Jun  8 21:43:54 localhost kernel: [4659913.445000] VFS: busy inodes on changed media.
Jun  8 21:43:54 localhost kernel: [4659913.829000] VFS: busy inodes on changed media.
Jun  8 21:43:54 localhost kernel: [4659913.836000] VFS: busy inodes on changed media.
Jun  8 21:43:56 localhost kernel: [4659915.454000] VFS: busy inodes on changed media.
Jun  8 21:43:56 localhost kernel: [4659915.461000] VFS: busy inodes on changed media.
Jun  8 21:43:56 localhost kernel: [4659915.844000] VFS: busy inodes on changed media.
Jun  8 21:43:56 localhost kernel: [4659915.851000] VFS: busy inodes on changed media.
Jun  8 21:43:58 localhost kernel: [4659917.469000] VFS: busy inodes on changed media.
Jun  8 21:43:58 localhost kernel: [4659917.475000] VFS: busy inodes on changed media.
```

Does anyone else see this in their log? (do tail -f /var/log/syslog). Does anyone know what it is? Googling for this turned up some hits, but nothing that helped me understand.

Thanks.

---

### Post by scxtt on 2006-06-08
this is all i have:

```
$:> cat /var/log/syslog | grep VFS
Jun  8 03:23:31 localhost kernel: [4294672.221000] VFS: Disk quotas dquot_6.5.1
Jun  8 07:05:28 localhost kernel: [4294668.205000] VFS: Disk quotas dquot_6.5.1
Jun  8 14:03:23 localhost kernel: [4294671.068000] VFS: Disk quotas dquot_6.5.1
Jun  8 15:34:50 localhost kernel: [4294671.388000] VFS: Disk quotas dquot_6.5.1
```granted, i don't really know what it means (checking disk quotas?) ...

---

### Post by mannheim on 2006-06-08
Does the message in my original post just mean I removed a disk (e.g a usb disk or a cdrom) that was mounted and busy?

If a CD is mounted, and I remove it just by pressing the eject button on the tray, am I asking for this sort of trouble? (I hope not.)

---

### Post by scxtt on 2006-06-08
i wouldn't say it's trouble, but as far as i'm aware most optical drives are "locked" until you unmount them (probably for sync issues) ... there's only an 8sec. time frame from what you posted (just a snippet?) -- is there more for extended periods of time (like minutes?) ...

---

### Post by mannheim on 2006-06-08
[QUOTE=scxtt]i wouldn't say it's trouble, but as far as i'm aware most optical drives are "locked" until you unmount them (probably for sync issues) ... there's only an 8sec. time frame from what you posted (just a snippet?) -- is there more for extended periods of time (like minutes?) ...[/QUOTE]

I think I've got about 2.5 days of that stuff (tens of megabytes of syslogs when uncompressed). A reboot just put an end to it! Perhaps tomorrow I'll try some experiments, like pulling out a busy usb drive, to see if I can find a reproducible cause.

Many thanks for your comments.

---

### Post by KYAAngel on 2006-06-28
The same error is my logs also.  Like 15 megs uncompressed of this stuff...  It might have started around the time I was booting up some vmware instances but that could be purely coincidental.

---

### Post by Snover on 2006-07-09
Apparently this happens if you eject a CD using the eject button on the drive. If you use the eject command, this does not happen. The solution (other than reboot) is to insert another CD and then use the eject command. :\

---

### Post by wirah on 2008-01-08
Just type mount

See what drive is mounted (and shouldn't be, in my case I had a cdrom mounted and there was no cd in the drive)  and 'sudo umount /dev/xxx' where xxx is your drive.

---

### Post by bitumen on 2008-07-08
I've just come across this error when vmserver with xp failed to load properly resulting in no network for the xp guest (rebooting to sort the issue)


OK, rebooted vmserver = no change 

BUT 

rebooted Ubuntu 8.04 host 
and this time when i reviewed the system log 
found that a cd that i had been using with the windows xp guest (that i manually removed),
was the last logical message in the logs

> Jul  8 11:08:38 ubuntu NetworkManager: <debug> [1215472118.229093] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_Partition_Saving'). 

where volume_label_Partition_Saving = CD label.

thus i conclude that removing the cd without ejection caused the issue

and i believe the network issue is totally separate.

---

