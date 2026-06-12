---
title: "File server"
date: 2011-09-27
forum: General Help
---

### Post by absentcrisis on 2011-09-27
I am trying to connect to my file server a ubuntu install using samba. Not sure what tools to use?

---

### Post by brucehohl on 2011-09-27
If you are using Ubuntu 10.04 LTS try this:
Places > Connect to Server:
Service type = Windows share
Server = <host name or IP of your Samba server>
Share  = <name of file share>
Add bookmark = Y
Bookmark name = <some name>

---

