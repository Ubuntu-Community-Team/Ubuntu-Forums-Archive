---
title: "Kernel Panic- not syncing:"
date: 2011-02-14
forum: General Help
---

### Post by Sparky250 on 2011-02-14
I am getting an error when I try to boot my ubuntu 10.4 system (64 bit). Error:Kernel Panic- Not syncing: VFS: Unable to mount root fs on unknown-block(0,0).


Here is some back ground info- I installed Sbackup and tried to create a backup of the home, var, usr/local folders. I started the backup and it ran for about 30 minutes then I got a message from the system that indicated that I was out of hard drive space, then the system froze. I restarted the system and then I got the above mentioned error.

-
And suggestions on how to recover would be helpful.

thanks.

---

### Post by Irihapeti on 2011-02-15
It sounds like sbackup was writing the backup to the same hard drive. The default destination directory is /var/backup.

If you have a live CD (or live USB) handy, boot with that and remove the file(s) from /var/backup (or other directory if you instructed it to backup elsewhere).

Then see if the system will boot from the hard drive.

---

