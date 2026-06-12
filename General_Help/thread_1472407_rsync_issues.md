---
title: "rsync issues"
date: 2010-05-04
forum: General Help
---

### Post by DaF1oh1 on 2010-05-04
Hi all,

I have a linux box thats running Ubuntu Server 8.04 (due for upgrade) and I am having issues with the rsync server that I have installed on it. What has happened is I have set up my rsyncd.conf so it looks like this

max connections = 3
log file = /var/log/rsync.log
timeout = 300

[user-storage]
        comment = Computer Storage Backup
        path = /data/backup/user-storage
        read only = yes
        list = yes
        uid = nobody
        gid = nogroup
        auth users = matt, root
        secrets file = /usr/local/etc/rsyncd.secrets
        hosts allow = 192.168.0.2, 192.168.0.3

But everytime I run the rsync, it doesn't go to the path that I have specified, it goes under the /root directory. 

Can anyone help?

---

