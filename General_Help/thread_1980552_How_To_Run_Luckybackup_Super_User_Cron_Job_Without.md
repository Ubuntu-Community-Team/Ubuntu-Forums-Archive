---
title: "How To Run Luckybackup Super User Cron Job Without Login"
date: 2012-05-15
forum: General Help
---

### Post by Precipitous on 2012-05-15
Is there a way to run a Luckybackup Super User cron job without being prompted to log in? Ever since upgrading to Precise - the only way I can get Luckybackup to work properly is by running the Super User version instead of the regular one. The regular version acts as though it is running OK, but no new files get written to the location it is set to write to, and I get an rsync broken pipe error...  The Super User version works perfectly.

---

### Post by papibe on 2012-05-16
Hi Precipitous.

Are you backing up locally or to a remote host?

Regards.

---

### Post by Precipitous on 2012-05-16
> **papibe said:**
> Hi Precipitous.

Are you backing up locally or to a remote host?

Regards.
I am backing up locally to an external USB drive.

---

### Post by papibe on 2012-05-16
It looks like a permissions problem.

Is it NTFS or something else? Remember that NTFS does not support users, and the permissions and ownership are set on the mount options.

Is it always mounted, or just for the backup? The command 'mount' requires root privileges (there is other ways to mount).

Do you have any directory set for privacy (like 000 permissions)? Even your user won't be able to write to those directories in case they are set that way.

Just some thoughts.
Regards.

---

### Post by Precipitous on 2012-05-16
> **papibe said:**
> It looks like a permissions problem.

Is it NTFS or something else? Remember that NTFS does not support users, and the permissions and ownership are set on the mount options.

Is it always mounted, or just for the backup? The command 'mount' requires root privileges (there is other ways to mount).

Do you have any directory set for privacy (like 000 permissions)? Even your user won't be able to write to those directories in case they are set that way.

Just some thoughts.
Regards.
The drive I am backing up to is formatted with ext4. The reason I am having to run Luckybackup Superuser is that ever since upgrading to Precise when I run Luckybackup as a regular user I get Rsync Broken Pipe errors and no files get written to the backup location.  Running as Superuser everything works fine. Although I can easily  run the backup manually I would like to be able to set it up as a Cron job that is totally automated. I just don't know how to do so without being prompted for a root login password.

---

### Post by papibe on 2012-05-16
You may create a crontab for root, instead of your regular user:
```
sudo crontab -e
```
That way you shouldn't have password issues.

Regards.

---

