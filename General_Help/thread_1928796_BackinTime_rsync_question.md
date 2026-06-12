---
title: "BackinTime rsync question"
date: 2012-02-20
forum: General Help
---

### Post by bluexrider on 2012-02-20
I had BackInTime-Gnome installed and was set up for periodic backups.

Since I have removed the application I have noticed:
1. Notifaction of low disk space on 'Filesystem root" 
2. Using TOP or Htop the "rsync" daemon is running. (using ROOT authorisation)

Question:

How do I kill and remove the rsync daemon.

---

### Post by papibe on 2012-02-21
Disable it by modifying the file /etc/default/rsync

change the line from:
```
RSYNC_ENABLE=inetd
```
to
```
RSYNC_ENABLE=false
```
then either kill the daemon, or restart your machine.

Hope it helps.
Regards.

---

### Post by bluexrider on 2012-02-21
> **papibe said:**
> Disable it by modifying the file /etc/default/rsync

change the line from:
```
RSYNC_ENABLE=inetd
```to
```
RSYNC_ENABLE=false
```then either kill the daemon, or restart your machine.

Hope it helps.
Regards.
Worked Thanks

---

