---
title: "Backing up with rsnapshot and alternating external HDD"
date: 2012-06-04
forum: General Help
---

### Post by sirvoo on 2012-06-04
Hi,

I am using ubuntu server 11.10 with rSnapshot;

I plan on alternating the backup external hdd every month.

I have setup for external hdd 1 to mount using it's UUID. I have to manually mount it every time I plug it in. The mount is to /media/backup_disk_1

The rsnapshot.conf:

snapshot_root /media/backup_disk_1/backup
no_create_root 1.


There is a hourly, daily, weekly and monthly cron job.

if I was to switch to the 2nd external hdd then I would need to setup another mount with it's UUID and mount to /media/backup_disk_2

then I would need to manually change the root location in rsnapshot.conf

snapshot_root /media/backup_disk_2/backup
no_create_root 1.

Is there an automated way to do this instead of changing the config file everytime I alternate between the hdd?

Will mounting both of the external hdd to /media/backup_disk_1 work?
So no matter which hdd I mount they will all mount to /media/backup_disk_1.

---

