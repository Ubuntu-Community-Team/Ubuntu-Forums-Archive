---
title: "cron format error"
date: 2009-10-06
forum: General Help
---

### Post by Gorlist on 2009-10-06
Hi, having a problem with one of my cron scripts, it will run fine if I excute it directly from bash, however when anacron tries to process during cron.daily, comes up with a "Exec format error" and exits with a return code 1. 

```
TIME=`date | (read u v w x y z; echo $u)`

#do backup
rm /var/dailybackup/backup*
/usr/local/psa/bin/pleskbackup --server --output-file=/var/dailybackup/backup-$TIME
#copy backup to FTP server

lftp backup.secured-ftp.com -u myusername,mypassword <<EOF
cd /
lcd /var/dailybackup/
put backup-$TIME
quit 0
EOF

```

I can't seem to find any error?

Best Regards,

---

### Post by rudy.b on 2009-10-06
Make sure that any scripts executed by cron start with the shebang line (e.g. #!/bin/sh or #!/bin/bash) and that they are executable by the owner of the crontab.

---

### Post by Gorlist on 2009-10-06
Thanks rudy :) knew it had to be something simple :)

---

### Post by rudy.b on 2009-10-06
Cool, glad to help. O:)

---

