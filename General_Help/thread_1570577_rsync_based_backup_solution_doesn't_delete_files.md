---
title: "rsync based backup solution doesn't delete files"
date: 2010-09-08
forum: General Help
---

### Post by morgan.beeby on 2010-09-08
Hi all,

I'm using cron to run rsync every night to backup from one hard drive to another. Unfortunately, I can't seem to get the [FONT=Courier New]--delete[/FONT] option to work through cron - although it seems to work just fine when I run rsync with the same arguments on test directories using my own user. This makes me think it's a user/permissions problem (although rsync is indeed copying the files as desired - it's just not deleting files on the backup drive which I've removed from the working drive).

The command I'm running is:

[FONT=Courier New]/usr/bin/rsync -avltr --delete /home/mbeeby /mnt/backup2[/FONT]

Does anyone have any ideas as to what I'm doing wrong?

Many thanks,

-Morgan

---

### Post by CharlesA on 2010-09-08
In order to use -a to apply the correct permissions/owners you would need to run it as root.

Does it work when you run it with sudo?

FYI: -a = -rlptgoD

You can run rsync like so:

```
rsync --archive --verbose --delete /home/mbeeby /mnt/backup2
```

I've got mine set to use -i (--itemize-changes) so that it will show me what it is doing, instead of using verbose mode.

EDIT: If you are just testing it to make sure it's deleting files, you can add --dry-run so that it doesn't actually modify anything.

---

