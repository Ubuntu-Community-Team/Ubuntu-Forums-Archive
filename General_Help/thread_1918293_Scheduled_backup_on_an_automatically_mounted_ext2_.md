---
title: "Scheduled backup on an automatically mounted ext2 partition"
date: 2012-01-31
forum: General Help
---

### Post by ABPAM on 2012-01-31
I am pretty new to Ubuntu, but recently I had to configure a Linux server. The disk is 120 GB and is in two partitions: 1 File system partition 60GB and another sda5 partition 60GB. This server is gonna be 12 km away from me and I would be able to administrate it only remotely. It has to automatically mount the sda5 drive and one time in 24 hours, to make a backup on the whole system (File system drive) on this sda5 partition. How could this be done?
Thanks in advance!

---

### Post by sj1410 on 2012-02-01
you can schedule to run any command using cron, you can run

```

crontab -e

```

to add or edit cron jobs

---

### Post by Paqman on 2012-02-01
You can use rsync to create the backup, and cron or anacron to carry it out. Since the server is likely to be on 24/7 you could use cron, but I find anacron much simpler to use. Simply drop your backup script into /etc/cron.daily and it will be run every 24 hours.

As for the script itself, rsync is a one-line command. You haven't been specific about your backup requirements though. I assume you intend to copy the whole of one partition to the other, replacing the data from the previous 24 hours? That's fine, but the obvious flaw is that your data is still sitting on the single drive. You'll need to back it up to another location to properly secure it.

---

### Post by drmrgd on 2012-02-01
I would definitely concur that leaving the backups on the main drive is dangerous.  Your backups will be useless if the drive fails.

Another tool to look into is [Rsnapshot]("http://rsnapshot.org/").  It uses rsync to make the backups and keeps several copies of it in rotation depending on how many you want.  For example, if you wanted a daily backup, you might have 7 copies of the backed up data for each day (although you can keep much less if you wanted), and on day 8, backup #1 will be overwritten.  It handles all of the heavy lifting for you and is really easy to configure.

---

