---
title: "No such file or directory"
date: 2012-07-06
forum: General Help
---

### Post by arnaudom on 2012-07-06
Trying to implement automysqlbackup on ubuntu server.

[COLOR=Red]Problem: script runs perfectly when run manually but get file not found error with cron file script.[/COLOR]

Details:

 /// location of main script /// /usr/local/bin
  [EMAIL="root@203-174-87-130:/etc/cron.daily"]root@203-174-87-130:/etc/cron.daily[/EMAIL]# cd  /usr/local/bin/
  root@203-174-87-130:/usr/local/bin# ls
  **automysqlbackup**
  
 /// location of conf file /// /etc/automysqlbackup/
  root@203-174-87-130:/root# cd /etc/automysqlbackup/
  root@203-174-87-130:/etc/automysqlbackup# ls
  _automysqlbackup.conf  **a****utomysqlbackup.conf**  README.txt
  
 /// launching the main script manually /// OK
  root@203-174-87-130:/root# **automysqlbackup**
  Invoking backup method.
  Parsed config file "/etc/automysqlbackup/automysqlbackup.conf"
  # Checking for permissions to write to folders:
  base folder / ... exists ... ok.
  backup folder /backup ... exists ... writable? yes. **Proceeding**.
  root@203-174-87-130:/root#
  
 /// file running script in cron /// /etc//cron.daily[INDENT]*#!/bin/sh*
*/usr/local/bin/automysqlbackup*
*#chown root.root /var/backup/db* -R*
*#find /var/backup/db* -type f -exec chmod 400 {} \;*
*#find /var/backup/db* -type d -exec chmod 700 {} \;*
[/INDENT] /// when launch script in cron or manual run /// ERROR
  [EMAIL="root@203-174-87-130:/etc/cron.daily"]root@203-174-87-130:/etc/cron.daily[/EMAIL]# sh run_mysql_backup.sh
  : not foundackup.sh: 2:
  : not foundackup.sh: 3: /usr/local/bin/automysqlbackup
  : not foundackup.sh: 4:
  : not foundackup.sh: 8:
  : not foundackup.sh: 9:
  
/// when the daily cron is started by server /// ERROR (note mysql_backup_v3 is a symlink to the above script file)[INDENT]/etc/cron.daily/mysql_backup_v3:
 run-parts: failed to exec /etc/cron.daily/mysql_backup_v3: No such file or directory
run-parts: /etc/cron.daily/mysql_backup_v3 exited with return code 1


[/INDENT]I can't figure out what is the issue here.Note I tried all possible syntax of the script file without success.

Thank you for help.

---

### Post by Toz on 2012-07-06
What do the following commands return:
```
ls -l /usr/local/bin/
```

```
ls -l /etc/cron.daily/
```

And what are the contents of **/etc/cron.daily/run_mysql_backup.sh**

---

### Post by arnaudom on 2012-07-06
Here it is.
I have already thought about permission, but I did not find a solution there...

root@203-174-87-130:~# ls -l /usr/local/bin/
total 92
-rwxr-xr-x 1 root root 89097 2012-07-05 09:37 automysqlbackup


root@203-174-87-130:~# ls -l /etc/cron.daily/
total 52
lrwxrwxrwx 1 root root   25 2009-01-06 11:12 documents_backup -> /root/documents_backup.sh
lrwxrwxrwx 1 root root   35 2012-07-05 14:41 documents_screening_backup -> /root/documents_screening_backup.sh
lrwxrwxrwx 1 root root   25 2012-07-07 10:13 mysql_backup_v3 -> /root/run_mysql_backup.sh
-rwxr-xr-x 1 root root  194 2012-07-07 06:33 run_mysql_backup.sh


the content of run_mysql_backup.sh in cron.daily is the same as in /root. I copied the file to test if it was a problem with symlink only.

for info:
[INDENT]*#!/bin/sh*
*/usr/local/bin/automysqlbackup*
*#chown root.root /var/backup/db* -R*
*#find /var/backup/db* -type f -exec chmod 400 {} \;*
*#find /var/backup/db* -type d -exec chmod 700 {} \;*[/INDENT]
Note: the other scripts/symlink that are here a working perfectly (backups using previous version of automysqlbackup) 

Thanks

---

### Post by Toz on 2012-07-07
Have a look at this post ([http://ubuntuforums.org/showpost.php?p=10154736&postcount=4]("http://ubuntuforums.org/showpost.php?p=10154736&postcount=4")) I think you might be affected by this issue.

---

### Post by arnaudom on 2012-07-07
Hi,
Thank you for your suggestion. I am looking at it.

However, technically, the file is executed outside cron. The purpose of the symlink apparently is to avoid the problem discribed in the post.

When I run run-parts --test /etc/cron.daily

I get positive response for the 3 symlinks

/etc/cron.daily/documents_backup
/etc/cron.daily/documents_screening_backup
/etc/cron.daily/mysql_backup_v3

mysql_backup_v3 being the culprit... and other 2 backups being excuted without problem outside cron in /root

---

### Post by arnaudom on 2012-07-07
I think I got the answer ....

when trying manual:

root@203-174-87-130:/root#  /etc/cron.daily/run_mysql_backup_v3

Got:

bash: /etc/cron.daily/run_mysql_backup_v3:[COLOR=Red] /bin/sh^M[/COLOR]: bad interpreter: No such file or directory

after re-editing a new file with nano and run again
root@203-174-87-130:/root#  /etc/cron.daily/run_mysql_backup_v3

Got:

Invoking backup method.

[INDENT][LEFT]Parsed config file "/etc/automysqlbackup/automysqlbackup.conf"
# Checking for permissions to write to folders:
base folder / ... exists ... ok.
backup folder /backup ... exists ... writable? yes. Proceeding.

[/LEFT]
[/INDENT]Which is what I need... So it seems it was a [COLOR=Red]unix style script error[/COLOR].

Thank you.
[LEFT]
[/LEFT]

---

