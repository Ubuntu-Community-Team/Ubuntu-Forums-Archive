---
title: "Backups, Rsync &amp; a Cron job"
date: 2010-04-25
forum: General Help
---

### Post by gaming_guy on 2010-04-25
Hi all,

I back my ubuntu box up to my NAS drive weekly. I've created a cron job via gnome-schedule which is set to backup the machine to /nasbackup (which is mounted via NFS) automatically at a set time.

The cron job command is:
```

rsync -r -t -z /home/user/ /nasbackup/user_home_folder_backup/ & echo "Backup Successful: $(date)" >> /home/user/Desktop/backup.log

```

When the job runs, it starts the backup fine (& completes the backup) however, it writes the backup successful message about a second after it starts the backup (I'm assuming because the 2 commands are combined). What i want to happen is for the cron job to run and to write the backup successful message to the file when the backup finishes.

Does anyone have any ideas to how I can accomplish this?

Thanks in advance :)

g_g

---

### Post by thebigob on 2010-04-25
because you are putting the job into the background the thread that is calling it will move straight onto the next job.

If you are running this from cron you dont actually need the & instead change this to a semi colon ";"

This will do the first command and wait till it is finished before running the second command.

---

### Post by ajgreeny on 2010-04-25
You can also use && to do the same thing, or you can in terminal, so I assume the same is true of a cron job.

---

### Post by gaming_guy on 2010-04-25
Thank you to both of you for replying :)

I used the method posted by thebigob and it worked fine.

Thanks again to all that replied :)

---

