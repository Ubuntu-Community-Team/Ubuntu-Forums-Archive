---
title: "Back in Time no longer works"
date: 2010-11-25
forum: General Help
---

### Post by castironpants on 2010-11-25
I've been using Back in Time on Maverick (originally on Karmic) for some time but in the last couple of weeks I haven't been able to make new backups. Here's my output:

```
[REDACTED: ~]$ backintime -b

Back In Time
Version: 1.0.4

Back In Time comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; type `backintime --license' for details.

INFO: Lock
INFO: [GnomePlugin.Systray.run]
INFO: on process begins
INFO: [GnomePlugin.Systray.run] begin loop
INFO: Profile_id: 1
INFO: Compare with old snapshot: 20101028-210227-523
INFO: Command "rsync -rtDH --checksum --links --no-p --no-g --no-o  --delete --delete-excluded  -i --dry-run --out-format="BACKINTIME: %i %n%L" --chmod=Du+wx  --exclude="/media/Backup" --exclude="/home/REDACTED/.local/share/backintime" --include="/home/REDACTED/" --include="/home/" --include="/etc/apt/" --include="/etc/" --include="/opt/" --include="/usr/share/pixmaps/" --include="/usr/share/" --include="/usr/" --include="/usr/local/bin/" --include="/usr/local/" --exclude="*.backup*" --exclude="*~" --exclude="/home/REDACTED/Videos/.private" --exclude="*.iso" --exclude="*.ISO" --exclude="/home/REDACTED/.local/share/Trash" --exclude="/home/REDACTED/.gvfs" --exclude=".cache*" --exclude="/home/REDACTED/.config/dconf" --include="/home/REDACTED/**" --include="/etc/apt/**" --include="/opt/**" --include="/usr/share/pixmaps/**" --include="/usr/local/bin/**" --exclude="*" / "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/"" returns 0
INFO: Create hard-links
INFO: Command "find "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/" -type d -exec chmod u+wx {} \;" returns 0
INFO: Command "cp -aRl "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/"* "/media/Backup/backintime/acer/REDACTED/1/new_snapshot/backup/"" returns 0
INFO: Command "find "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/" -type d -exec chmod a-w {} \;" returns 0
INFO: Command "chmod -R a+w "/media/Backup/backintime/acer/REDACTED/1/new_snapshot"" returns 0
INFO: Call rsync to take the snapshot
WARNING: Command "rsync -rtDH --checksum --links --no-p --no-g --no-o  --delete --delete-excluded  -v  --chmod=Du+wx  --exclude="/media/Backup" --exclude="/home/REDACTED/.local/share/backintime" --include="/home/REDACTED/" --include="/home/" --include="/etc/apt/" --include="/etc/" --include="/opt/" --include="/usr/share/pixmaps/" --include="/usr/share/" --include="/usr/" --include="/usr/local/bin/" --include="/usr/local/" --exclude="*.backup*" --exclude="*~" --exclude="/home/REDACTED/Videos/.private" --exclude="*.iso" --exclude="*.ISO" --exclude="/home/REDACTED/.local/share/Trash" --exclude="/home/REDACTED/.gvfs" --exclude=".cache*" --exclude="/home/REDACTED/.config/dconf" --include="/home/REDACTED/**" --include="/etc/apt/**" --include="/opt/**" --include="/usr/share/pixmaps/**" --include="/usr/local/bin/**" --exclude="*" / "/media/Backup/backintime/acer/REDACTED/1/new_snapshot/backup/" 2>&1" returns 3072
INFO: Command "find "/media/Backup/backintime/acer/REDACTED/1/new_snapshot" -type d -exec chmod u+wx {} \;" returns 0
INFO: Command "rm -rf "/media/Backup/backintime/acer/REDACTED/1/new_snapshot"" returns 0
INFO: Command "chmod -R a-w "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/"" returns 0
INFO: Command "rm -rf "/media/Backup/backintime/acer/REDACTED/1/20101124-131225-523"" returns 0
ERROR: Failed to take snapshot !!!

** (backintime.py:6230): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed

** (backintime.py:6230): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed
INFO: [GnomePlugin.Systray.run] end loop
INFO: Unlock
[REDACTED: ~]$
```

---

### Post by ptn107 on 2010-11-25
Should you be using 'sudo'?

---

### Post by castironpants on 2010-11-25
When they first upgraded it to show all the errors, they recommended using it as root so I did. It was when using it as root that I first encoutered the problem. I tried going back but I get the same error message either way. No dice. I may try reinstalling it.

EDIT: Ok, I actually just tried root again saving to a different snapshot folder so there are no previous snapshots and that seems to have done it. I don't love it and it's not a perfect solution, but at least I'm backed up.

---

