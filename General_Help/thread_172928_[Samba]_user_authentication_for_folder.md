---
title: "[Samba] user authentication for folder"
date: 2006-05-09
forum: General Help
---

### Post by brechtvb on 2006-05-09
smb.conf

[FONT="Courier New"]
[global]
        securty = share
        browsable = yes
        workgroup = MSHOME
        log file = /var/log/samba/log.%m
        log level = 2
        max log size = 100

[webserver]
        path= /var/www/
        valid users = brecht
        writable = yes
[/FONT]

smbpasswd.conf

[FONT="Courier New"]
nobody:65534:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[DU         ]:LCT-00000000:
brecht:1000:50BAA7408FD9FBC6A49DC3F590CCA23D:E790B8AC2473CE4E70E248906B7063BD:[U          ]:LCT-4460D432:
root:0:50BAA7408FD9FBC6A49DC3F590CCA23D:E790B8AC2473CE4E70E248906B7063BD:[U          ]:LCT-4460CF6B:
[/FONT]

i can see the folder "webserver" but i can't get in to it, i can asure you i'm using the right password and username

i never get access to the folder

---

