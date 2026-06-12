---
title: "Can See But Can't Open Samba Folder"
date: 2010-11-01
forum: General Help
---

### Post by sky1174 on 2010-11-01
I can see samba share folder from my XP network neighborhood (my XP join to win server 2003 domain) but when I double click those folder there is a message folder not accessable more data is available.

I install Samba 4 on UBuntu 9.1

Thanks

---

### Post by luvshines on 2010-11-01
Downgrade to Samba 3 and make sure the shared path is readable by the user by which you are trying to connect(ie each of the directory starting from / upto the shared path)

---

