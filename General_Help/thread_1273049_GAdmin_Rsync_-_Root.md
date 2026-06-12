---
title: "GAdmin Rsync - Root?"
date: 2009-09-22
forum: General Help
---

### Post by Roasted on 2009-09-22
If I would set up an rsync backup through GAdmin Rsync, does it run it as root?

Reason I ask is I currently run my rsync backups via a script I wrote + crontab. 

If the drive is unmounted, the mount point (/media/storage) is owned by root.
If the drive is mounted, the mount point is owned by jason.

The script I wrote doesn't run as root, so that way if the drive becomes unmounted due to it dying or whatever, the script won't push my data to /media, because we all know if /media/storage is Drive B, but Drive B isn't there, it then gets tagged to root on Drive A.... therefore 500gb of data would max out my 20gb root partition rather quickly.

Anyway, does GAdmin Rsync run as root or no?

ALSO - Does Gadmin check if the drive is mounted first prior to running??

---

### Post by redmk2 on 2009-09-23
> **Roasted said:**
> If I would set up an rsync backup through GAdmin Rsync, does it run it as root?

Reason I ask is I currently run my rsync backups via a script I wrote + crontab. 

If the drive is unmounted, the mount point (/media/storage) is owned by root.
If the drive is mounted, the mount point is owned by jason.

The script I wrote doesn't run as root, so that way if the drive becomes unmounted due to it dying or whatever, the script won't push my data to /media, because we all know if /media/storage is Drive B, but Drive B isn't there, it then gets tagged to root on Drive A.... 
Not unless YOU wrote the script that way. Good practice would be to use absolute paths in your scripts.> 
therefore 500gb of data would max out my 20gb root partition rather quickly.


Anyway, does GAdmin Rsync run as root or no?
Dunno, never used GAdmin.> 

ALSO - Does Gadmin check if the drive is mounted first prior to running??

Your script should be written to check before continuing.  I add a readme file to the mount point directory.  This file explains to others what the mount point is for and I test for its existence in my backup script.  If the file is found then the drive is NOT mounted and the script echos that fact to STDOUT and halts.  If the readme file CAN NOT be found then the drive is mounted and the backup continues.

---

### Post by Roasted on 2009-10-18
So more or less, how would I set it up so my system verifies the drive is mounted prior to executing the rsync script? My drives mount automatically via fstab, but if I have a drive go down randomly, I don't want the script forcing 380gb of data to still hit the mount point, which /media/backup is on my root directory unless otherwise mounted. So, if drive dies, mount point then resides on root directory, and root directory is only 20gb, so forcing 380gb on it = problem. Granted, I guess it's no big deal cause I could just delete the data then if it happens (or delete it from a LiveCD boot) but, still. I'd like to avoid that possibility if at all possible.

---

