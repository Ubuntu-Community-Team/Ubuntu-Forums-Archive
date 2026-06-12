---
title: "SBackup no longer schedules backups"
date: 2012-02-10
forum: General Help
---

### Post by ibates on 2012-02-10
Ubuntu 10.10 LTS fully updated.

I have been running Simple Backup for well over a year very successfully, backing up to an external USB HDD.  It does automatic backups based on a standard daily backup schedule.

Recently, I installed an NAS and want to backup to that network device.

I can do manual backups just fine, but Simple Backup, although it finds the network drive (the NAS), it will not execute scheduled backups.

Why would this be?  Nothing has changed except the destination of the backup which gets the green tick when tested in Simple Backup.

---

### Post by ibates on 2012-02-13
Further to the above, the problem may be that I am setting the destination as "smb://nas-xx-xx-xx/backup/destination-directory/" using the smb protocol.

Is this allowed?  Or must I use the ssh:// or ftp:// protocol?

If so, then how do I configure the above destination using say, the ssh:// protocol.  I do not understand the example given in the sbackup documentation "ssh://username:password@example.com/remote/dir/"

Assistance would be appreciated.

---

