---
title: "dd question"
date: 2012-04-10
forum: General Help
---

### Post by sr_guy on 2012-04-10
I want to start doing nightly backups of existing data on my drive as a compressed image(s) using dd. It's a live server, so I want to do the backup with a small script and cron. So, my question is, do I need to unmount the drive being backed up, or will killing lightdm be sufficient not to cause problems with live processes while the backup is running or does it matter that the drive being backup is mounted and running ubuntu while it's being backed up with dd?

---

### Post by dcstar on 2012-04-11
> **sr_guy said:**
> I want to start doing nightly backups of existing data on my drive as a compressed image(s) using dd. It's a live server, so I want to do the backup with a small script and cron. So, my question is, do I need to unmount the drive being backed up, or will killing lightdm be sufficient not to cause problems with live processes while the backup is running or does it matter that the drive being backup is mounted and running ubuntu while it's being backed up with dd?

Using something like dd to back up running & mounted systems will only result in a useless backup.

Use the proper tools like rsync and the things that use it for backups - that is what they were created for.

---

### Post by kimda on 2012-04-11
Another tool you might wat to look at is rsnapshot. It can make hourly, daily, weekly and monthly backups of your data.

---

