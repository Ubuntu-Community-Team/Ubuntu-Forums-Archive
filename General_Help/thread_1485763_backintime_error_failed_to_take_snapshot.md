---
title: "backintime error: failed to take snapshot"
date: 2010-05-17
forum: General Help
---

### Post by houserparker on 2010-05-17
Hi there,

Since updating backintime from the BIT team ppa to try and rectify another problem, backintime hasn't been able to complete a snapshot without returning the following:-

error: failed to take snapshot

output of backintime -b is a follows:-

Can someone help me translate this?


ben@ben-laptop:~$ backintime -b

Back In Time
Version: 0.9.99.37

Back In Time comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; type `backintime --license' for details.

ABC:
[]
INFO: Lock
INFO: on process begins
INFO: Profile_id: 1
INFO: [GnomePlugin.Systray.run]
INFO: [GnomePlugin.Systray.run] begin loop
ABC:
[]
INFO: Call rsync to take the snapshot
WARNING: Command "rsync -aEH  --delete --delete-excluded  -v  --chmod=Da+w  --exclude="/media/DATA" --exclude="/home/ben/.local/share/backintime" --include="/home/ben/" --include="/home/" --include="/media/Data/" --include="/media/" --exclude=".*" --exclude="*.backup*" --exclude="*~" --include="/home/ben/**" --include="/media/Data/**" --exclude="*" / "/media/DATA/backintime/ben-laptop/ben/1/new_snapshot/backup/" 2>&1" returns 5888
INFO: Command "find "/media/DATA/backintime/ben-laptop/ben/1/new_snapshot" -type d -exec chmod u+wx {} \;" returns 0
INFO: Command "rm -rf "/media/DATA/backintime/ben-laptop/ben/1/new_snapshot"" returns 0
INFO: Command "rm -rf "/media/DATA/backintime/ben-laptop/ben/1/20100517-191133-736"" returns 0
ERROR: Failed to take snapshot !!!
INFO: [GnomePlugin.Systray.run] end loop
INFO: Unlock

** (backintime.py:19061): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (backintime.py:19061): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed
ben@ben-laptop:~$

Thanks,

---

### Post by castironpants on 2010-11-24
I am having a very similar problem. Here's my output:

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
'

rsync: readlink_stat("/home/REDACTED/.config/dconf/user") failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
WARNING: Command "rsync -rtDH --checksum --links --no-p --no-g --no-o  --delete --delete-excluded  -i --dry-run --out-format="BACKINTIME: %i %n%L" --chmod=Du+wx  --exclude="/media/Backup" --exclude="/home/REDACTED/.local/share/backintime" --include="/home/REDACTED/" --include="/home/" --include="/etc/apt/" --include="/etc/" --include="/opt/" --include="/usr/share/pixmaps/" --include="/usr/share/" --include="/usr/" --include="/usr/local/bin/" --include="/usr/local/" --exclude="*.backup*" --exclude="*~" --exclude="/home/REDACTED/Videos/.private" --exclude="*.iso" --exclude="*.ISO" --exclude="/home/REDACTED/.local/share/Trash" --exclude="/home/REDACTED/.gvfs" --exclude=".cache*" --include="/home/REDACTED/**" --include="/etc/apt/**" --include="/opt/**" --include="/usr/share/pixmaps/**" --include="/usr/local/bin/**" --exclude="*" / "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/"" returns 5888
INFO: Create hard-links
INFO: Command "find "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/" -type d -exec chmod u+wx {} \;" returns 0
INFO: Command "cp -aRl "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/"* "/media/Backup/backintime/acer/REDACTED/1/new_snapshot/backup/"" returns 0
INFO: Command "find "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/" -type d -exec chmod a-w {} \;" returns 0
INFO: Command "chmod -R a+w "/media/Backup/backintime/acer/REDACTED/1/new_snapshot"" returns 0
INFO: Call rsync to take the snapshot
WARNING: Command "rsync -rtDH --checksum --links --no-p --no-g --no-o  --delete --delete-excluded  -v  --chmod=Du+wx  --exclude="/media/Backup" --exclude="/home/REDACTED/.local/share/backintime" --include="/home/REDACTED/" --include="/home/" --include="/etc/apt/" --include="/etc/" --include="/opt/" --include="/usr/share/pixmaps/" --include="/usr/share/" --include="/usr/" --include="/usr/local/bin/" --include="/usr/local/" --exclude="*.backup*" --exclude="*~" --exclude="/home/REDACTED/Videos/.private" --exclude="*.iso" --exclude="*.ISO" --exclude="/home/REDACTED/.local/share/Trash" --exclude="/home/REDACTED/.gvfs" --exclude=".cache*" --include="/home/REDACTED/**" --include="/etc/apt/**" --include="/opt/**" --include="/usr/share/pixmaps/**" --include="/usr/local/bin/**" --exclude="*" / "/media/Backup/backintime/acer/REDACTED/1/new_snapshot/backup/" 2>&1" returns 3072
INFO: Command "find "/media/Backup/backintime/acer/REDACTED/1/new_snapshot" -type d -exec chmod u+wx {} \;" returns 0
INFO: Command "rm -rf "/media/Backup/backintime/acer/REDACTED/1/new_snapshot"" returns 0
INFO: Command "chmod -R a-w "/media/Backup/backintime/acer/REDACTED/1/20101028-210227-523/backup/"" returns 0
INFO: Command "rm -rf "/media/Backup/backintime/acer/REDACTED/1/20101124-092657-523"" returns 0
ERROR: Failed to take snapshot !!!

** (backintime.py:6890): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed

** (backintime.py:6890): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed
INFO: [GnomePlugin.Systray.run] end loop
INFO: Unlock
[REDACTED: ~]$ '

```

---

### Post by geidorei on 2011-06-04
Hi - me too, thought it would be better than DejaVu but just fails every time. Ummmm update needed I think.

---

### Post by ParadoxBlue on 2011-08-04
Yup same story here. :confused: I had it working fine and don't even know why I upgraded it. I tried backing up to two different flash drives and same story on each. Hundreds and hundreds of "Operation Not Permitted" errors among a few errors. Has anyone tried a complete removal and then a re-install? And I forget...is the older version in the Ubuntu repo's?

---

### Post by ottosykora on 2011-08-04
OH, is that problem due to an update of backintime or is it connected with upgrade of ubuntu?

For me the backintime was fine for years up to 10.10 32bit

As the 11.04 32bit refused to work on my computer , I had to make fresh install of 11.04 64bit and installed backintime and it makes same problem as described.

It does not matter where I try to save the backup file, it simply fails, it creates some folders, but all are empty.

It this happening on 32bit now too?

---

### Post by ottosykora on 2011-08-05
I managed to find a solution, thought it is kind of strange.

The current version of backintime insists to store snapshot files so that the permissions are preserved. This seems to be solved now in a special file contending all information, but from now on all snapshots have to be stored on a media with permissions ability.

So in other word, it works fine on any linux formated partition, like ext3 , ext4, but also fine on ntfs formated partition. 
It does not work on any fat formated partition or device however.

---

### Post by ParadoxBlue on 2011-08-06
> **ottosykora said:**
> I managed to find a solution, thought it is kind of strange.

The current version of backintime insists to store snapshot files so that the permissions are preserved. This seems to be solved now in a special file contending all information, but from now on all snapshots have to be stored on a media with permissions ability.

So in other word, it works fine on any linux formated partition, like ext3 , ext4, but also fine on ntfs formated partition. 
It does not work on any fat formated partition or device however.

That would explain why the snapshots failed on either of my flash drives since I have them both formatted to FAT. I guess I can re-format them to NTFS as I would still like the backup info to be readable by Linux or Windows just in case.

---

### Post by ottosykora on 2011-08-06
yes, there is some not very clear statement on the website of the authors of the backintime, it is kind of misleading, as it says the permissions are stored in special file, but then this would not mean it should not work. But after testing it, looks like they are storing permissions information in the ntfs files system or if it meets some ext3 or so it will store it linux native format.

It is kind of advantage, but on the other hand, we do not care that much of permissions on pure data files in general. So I think this is just some kind of 'security' feature which makes many people wonder what it is about . Particularly because the error message produced does not give much clue as what does happen.

---

