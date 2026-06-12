---
title: "Samba Error: not set up to establish connection on port &quot;file and printer sharing (sm"
date: 2009-08-03
forum: General Help
---

### Post by l3l0uch on 2009-08-03
Trying to set up a ubuntu file server with an old pc. I keep running into this error:
[server name] not set up to establish connection on port "file and printer sharing (smb)"


here is my /etc/samba/smb.conf


[hda public hard disk]
comment = Public Folder
path = media/store
browsable = yes
guest ok = yes
read only = no
create mask = 0755
directory mask = 0700


please help!!

---

