---
title: "Access Permissions Over LAN"
date: 2011-06-22
forum: General Help
---

### Post by Keith W on 2011-06-22
I use an elderly Pentium III machine, with Xubuntu, as a backup machine.   My XP machine and my wife's XP machine backup to it over the LAN.

The backups are to two partitions on the Linux machine and these are the two lines in fstab that set it up

UUID=24E44887E4485D64 /media/BackupKW ntfs utf8,unmask=000
UUID=D4D46EDFD46EC37A /media/BackupDW ntfs utf8,unmask=000

I can access the partition BackupKW from the XP machines and run backups perfectly well but, although the partition BackupDW is viewable, any attempt to write to it is met with a message that access is denied.

What am I missing please?

---

### Post by Toz on 2011-06-22
How are you accessing these partitions from the XP boxes? Samba? If so, can we see the relevant sections from your samba config file?

If you are using samba, for the accounts that are accessing these shares, have you created samba accounts for them (smbpasswd -a)?

And finally, what do the permissions for these two mount points look like?```
ls -l /media/Backup*
```

---

### Post by Keith W on 2011-06-23
Many thanks, you solved it for me.   I am very much a Linux novice and set this up some time ago with help on this forum but apparently only tested the one drive.  Since then I had completely forgotten about smb.conf.  On your suggestion I looked in it and realised that one item, writeable, was set to yes on the drive that worked and no on the other.   Set that to yes and all is working.   Thanks again.

---

