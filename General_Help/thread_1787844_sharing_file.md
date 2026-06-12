---
title: "sharing file"
date: 2011-06-21
forum: General Help
---

### Post by grey_ghost on 2011-06-21
hi,
i want to share a folder with windows using samba server,i have made all the necessary changes in smb.conf file but when i clik on share option of the folder ,it give me  the folllowing messages

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Memory allocation error.


can anyone tell me why this error is coming and how i can remove this?

Thanks in advance

---

### Post by luvshines on 2011-06-22
Make sure smb service is running```
 sudo service smb status
```

---

### Post by crispy_420 on 2011-06-22
Are you editing the file file by hand? Do you want to post that section of the /etc/samba/smb.conf because it looks like a syntax error. I am assuming the share is on a Linux box after all. Also isn't "Everyone" listed as guest in samba unless you setup it up yourself?

---

### Post by grey_ghost on 2011-06-23
@luvshines, hi i have used the command but its showing the smb: unrecognized services,but when i used samba4 instead of smb then it showed the following:
[U][B]
Usage: /etc/init.d/samba {start|stop|restart|force-reload}[/B][/U]

---

### Post by grey_ghost on 2011-06-23
@crispy, yea ia m editing the smb.conf file using vim editor,and in the file i am allowing  guest access, and the following is the changes made to the smb.conf file

[share]
comment = My sharing flies
path = /home/manak/Desktop/share
guest ok = yes
read only = no
browseable = yes

---

