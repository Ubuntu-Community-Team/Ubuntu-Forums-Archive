---
title: "Script for MySQL backup?"
date: 2011-08-05
forum: General Help
---

### Post by Sarteck on 2011-08-05
I'd like to make a cron to backup one of my MySQL databases nightly.

It should:
 -- Rename the existing Backup file from **backup_db.sql.gz** to **backup_db.sql.gz.bak**
 -- Execute **mysqldump -u MyUserName -h localhost -p MyPassword MyDBName | gzip -9 > /path/to/my/backup/directory/backup_db.sql.gz**
 -- After the backup successfully completes, Remove the **backup_db.sql.gz.bak** backup

This should be in a shell script (I guess?) and executed from the crontab (I suppose?)

However... I'm not too familiar with making scripts.  Is it as simple as just putting the three commands in a text file, saving it as MyScript.sh, chmod'ing it +x, and then running it by **sh MyScript.sh**?  Or do I gotta add one of them SheBang things in there?  Or what?

Thanks in advance. :>

---

### Post by Wim Sturkenboom on 2011-08-05
You need the #! if you want to use it as you in indicate. As an alternative, you can use *_sh youscript.sh_*; in the latter case the script does not have to be executable.

Not a cron man, so can't help there.

One note
Create a mysql user that can only make backups (*select* and *lock tables* privileges on the specific databse or on all databases are enough as far as I know). That way you don't have to specify a password that can be revealed.

---

### Post by Sarteck on 2011-08-05
Thanks, did as you suggested with the extra user with only LOCK TABLES and SELECT privileges.  Ran the script as **sh /path/to/script.sh** and everything worked fine.

I created a crontab entry with the command as **sh /path/to/script.sh**, too, so I'll see if that works out for me.

---

### Post by Wim Sturkenboom on 2011-08-05
When you're happy with the result, please mark the tread as solved using the thread tools just above the first post.

---

