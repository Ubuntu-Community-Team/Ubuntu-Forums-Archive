---
title: "Backing up to a samba location"
date: 2010-01-12
forum: General Help
---

### Post by JigglyWiggly_ on 2010-01-12
How do I make scheduled backups to be saved to a samba location? I see no software that can handle smb://

Anyone got any ideas?

---

### Post by falconindy on 2010-01-13
Mount the remote share through [Samba]("https://help.ubuntu.com/community/SettingUpSamba") as CIFS or SMBFS.

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by Andreas1 on 2010-01-13
...and then use *rsync*, or *grsync* (if you want graphical interface) for doing the backup.
for scheduling this you can use *cron*, i think, but i haven't tried that, just search for it and you will know more.

here's an example for rsync:

```
rsync -ahnv --delete /my/folder /my/sambamountpoint (=simulation run)
rsync -ahv --delete /my/folder /my/sambamountpoint

```
for more info: man rsync

---

