---
title: "Problem with tar and verify"
date: 2009-09-18
forum: General Help
---

### Post by Azdour on 2009-09-18
Hi all,

I've got a backup script that runs each night to backup my data using the following tar command:

tar -cvpf --listed-incremental=$INCREMENTAL_LIST $BACKUP_CONTENTS >> $BACKUP_LOG

I create one full backup each week, and then an incremental backup for the other days.

This is working good, and once in a while I do a full restore on a test machine to check we have a restorable backup.

It has now come to the point that when I do the restore I cannot check all the files by hand as the backup has grown.

I saw that there is a verify parameter in tar so I changed my script to:

tar -cvpWf --listed-incremental=$INCREMENTAL_LIST $BACKUP_CONTENTS >> $BACKUP_LOG

My problem is that when it runs overnight, the backup.log only contains 4 verify lines as if it has stopped after the fourth directory - but there are no errors in the log.

I've run the script on a test machine and the backup.log contains all the verify output, but when it runs on the real machine I do not get all the verify lines I'm expecting...

Is there anything further I can do to debug and work out why the script does not verify on my machine? Are there other logs I should be looking at? If a cronjob hits an error where does it output the error to?

Thanks in advance.

---

