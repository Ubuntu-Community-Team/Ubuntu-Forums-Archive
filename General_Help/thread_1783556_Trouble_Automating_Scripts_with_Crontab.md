---
title: "Trouble Automating Scripts with Crontab"
date: 2011-06-15
forum: General Help
---

### Post by emufordinner on 2011-06-15
Hi All,

Hopefully this is the most appropriate section for my question. 

I have two scripts in use to 1) dump a sql instance to a local directory and 2) tar some files to an SMB share.  Both scripts write a few lines to a log I created in /var/log in addition to their main functions.  Everything runs great when I execute them manually, but when they run via cron I have a few unexpected results.  The problems are that the sql dump script fails to write everything to the log.  That is, it echoes `date`, but fails to print the $SIZE variable as you can see in the script below.  The tarfile script runs and prints $SIZE to the log, but it only transfers 4889KB.  Always 4.8M when run by cron.  When run manually, the tarfile averages around 1GB.

Here is the sql script - with minor edits, of course.
```

#! /bin/bash
SIZE=$1
echo `date` SQL Dump Started >> /var/log/backup.log
if [ -d /home/emu/backup/ ] ; then
/usr/bin/mysqldump \
--user=root \
--password=password \
--all-databases -c | \
/bin/gzip -9 > \
/home/emu/backup/`date +%Y%m%d`.tar.gz
else
echo "Target directory /home/emu/backup ain't thar." >> /var/log/backup.log
fi
echo `date` SQL Dump Finished >> /var/log/backup.log
: ${SIZE:=$(ls -lah backup/ | grep `date +%Y%m%d` | awk '{print $5}')}
echo "The size of `date +%Y%m%d`.tar.gz is $SIZE" >> /var/log/backup.log

```

And the tarfile script
```

#! /bin/bash
SIZE=$1
echo `date` Tardump Started >> /var/log/backup.log
if [ -f /mnt/smbserver/DoNotDelete.txt ] ; then
tar cvpzf /mnt/smbserver/`date +%Y%m%d`-wiki-backup.tar.gz \
--exclude=/proc \
--exclude=/lost+found \
--exclude=/mnt \
--exclude=/sys /
else
echo "Can't see SMBServer!" >> /var/log/backup.log
fi
echo `date` Tardump Finished >> /var/log/backup.log
: ${SIZE:=$(ls -lah /mnt/smbserver/ | grep `date +%Y%m%d` | awk '{print $5}')}
echo "The size of the wiki backup is $SIZE" >> /var/log/backup.log

```
As you can perhaps tell, I'm new to scripting.  As such, my goal here is to learn why I'm getting different results when executing these versus scheduling them, though pointers for improving the scripts would also be appreciated.

Some more relevant info; this is all happening on a 10.04 x64 server install.  The SMB share is mounted by fstab
```

//192.168.50.50/Backups/Tarfile-dir /mnt/smbserver smbfs credentials=/home/emu/.credfile,gid=backup    0       0

```
And crontab is configured thusly
```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
30 22   * * *   root    /home/emu/tardump.sh
10 18   * * *   root    /home/emu/sqldump.sh
#

```

Thanks in advance

---

### Post by emufordinner on 2011-06-17
bump > Any ideas anybody?  Or, perhaps a recommendation for a more scripting-centric place to look for help?

---

### Post by Habitual on 2011-06-18
try asking here, they are very wise and helpful.
[http://www.unix.com/shell-programming-scripting/](http://www.unix.com/shell-programming-scripting/)

---

### Post by emufordinner on 2011-06-27
I'll check in there.  Thanks for the tip.

---

