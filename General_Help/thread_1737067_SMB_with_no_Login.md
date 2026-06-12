---
title: "SMB with no Login"
date: 2011-04-23
forum: General Help
---

### Post by Don0918 on 2011-04-23
I am currently tinkering with my SMB configuration in my home server. My purpose is to enable users in the network to view, browse and edit files I decided to share. However, I would like them to do just plain old connect and open the folders without the server asking them for a username and password.

Is this possible? Thanks!

---

### Post by shadowlmd on 2011-04-23
Yes, it's possible. This is an example enty for smb.conf:

[Incoming]
   path = /tmp/incoming
   browseable = yes
   read only = no
   guest ok = yes
   guest only = yes
   create mask = 0644
   directory mask = 0755

Parameter "guest only" is not necessary, it just ensures every file in this share will be created by user "nobody" even if user is authenticated.

---

### Post by Don0918 on 2011-04-23
Hey! Thanks for this! Will try this in a while.

---

### Post by Don0918 on 2011-04-23
I'm guessing that I need to set permissions to the folders I am declaring in the **path = ' '** statement, right?

Follow-up question:
what are the **create mask** and **directory mask** attributes for?

---

### Post by shadowlmd on 2011-04-23
Yes, you must grant user nobody write permissions. In other words, `chown nobody /path/to/share`. Masks are file and directory creation masks. Read man chmod for more info.

---

