---
title: "How to map domain users to local users group?"
date: 2011-05-27
forum: General Help
---

### Post by GNU/Linux_Rocks! on 2011-05-27
Hi!
   
  Is there a way how to map all domain users form group „Domain Users“ to local group „users“ (and maybe some more)? I’m using Ubuntu 10.04 x32. It’s connected to my domain using Samba and Winbind, I can login using my domain credentials, automatically map user folder form DFS server, but I think that domain users have too much priviledges in the system and want to restrict them as much as possible…
   
  Any help will be greatly appreciated.  :D

---

### Post by GNU/Linux_Rocks! on 2011-05-27
I found something about PAM module pam_group and I thought that it could solve my problem by making every new user member of groups defined in /etc/security/group.conf. But there is warning that this may be insecure in the group.conf file. So I don’t know: to use it or not to use it, there is a question… :-P
   
  (I also tried using: sudo adduser “DOMAIN\Domain\ Users” users (and many different variants), but it was just a desperate attempt and it failed of course saying there is no user ‘DOMAIN\Domain\ Users’…)
   
Any idea how to solve this, please?

---

### Post by GNU/Linux_Rocks! on 2011-05-29
Did I do something wrong that no one answers me? If I did tell me so I can retrieve it...

---

