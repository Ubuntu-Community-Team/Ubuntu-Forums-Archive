---
title: "USB hard drive doesn't mount automatically"
date: 2010-05-28
forum: General Help
---

### Post by curdog on 2010-05-28
The other day a power outage affected an SSH server I have running 9.04 (32-bit desktop ed.).  I have two external USB hard drives used for cron-scheduled backups (one for rsync, one for an incremental) that are connected at all times.  When I reboot, they no longer mount automatically until I login to the gnome desktop.  As far as I can remember, they always mounted automatically before as disk-1 and disk-2, but now I have to login to the gnome desktop and then log back out.

I never had them listed in the fstab before since they just worked, & hope to avoid doing it this way since the drives sometimes get their paths (sdd and sde) interchanged.  However, is the best way to fix this to use UUIDs in fstab vs. using sde or sdd?  (such as in this post: [http://ubuntuforums.org/showthread.php?t=1432413&highlight=external+hard+drives+don't+mount+boot]("http://ubuntuforums.org/showthread.php?t=1432413&highlight=external+hard+drives+don't+mount+boot")  Or maybe I'm just remembering incorrectly & ubuntu doesn't mount them automatically until login?  Sometimes I have to reboot remotely, & this problem would cause the rsync to fill up my system drive.  Any ideas?  Thanks.

---

### Post by DagMan on 2010-05-29
From what you've said, I'd think that using UUID's in fstab would be the way to go.  They'lle mount earlier on in the boot process when everything else does.  You'll just have to make sure you have them at the correct mount points in fstab after you set it up the first time and then that should hopefully be the end of it.

---

### Post by curdog on 2010-05-30
Thanks, I'll give it shot then in the next couple days.

---

