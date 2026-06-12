---
title: "client/server share readwrite issue"
date: 2010-02-14
forum: General Help
---

### Post by linuxcss on 2010-02-14
running karmic 

have server1 (karmic)  shareB
have files in shareB  with owner:admin1  group:group1
also used gui to set group1 to have read write access
and smbpasswd too


have client1  machine also karmic mounting in /etc/fstab  server1  shareB
//server1/shareB  /media/shareB   cifs  username=group1,password=group1pasword,rw

the client mounts shareB  and I can see files and traverse directories however it will NOT
allow me to create files

what am I missing?

---

