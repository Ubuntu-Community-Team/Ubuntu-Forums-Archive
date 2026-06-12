---
title: "NX Server max users on  Karmic Server"
date: 2009-12-26
forum: General Help
---

### Post by Diverted Income on 2009-12-26
So is there a way to increase the number of maximum NX Clients from two to say 5? I tried removing the comment in the the server config file for NX and then it went to one user! Maybe I did something wrong?? It should have been 20 users then. 
Thanks!

---

### Post by jonest1 on 2009-12-26
I'm not sure if this is what you are looking for and I do not have NX experience.  I found this item at [http://www.nomachine.com/documents/admin-guide.php](http://www.nomachine.com/documents/admin-guide.php)

If the subscription type allows unlimited connections, the default configuration of NX server permits 20 concurrent connections. 
You can increase the maximum number of concurrent sessions by setting a reasonable value in the following configuration key in /usr/NX/etc/server.cfg:
SessionLimit = "20"

I hope this helps.

---

### Post by Diverted Income on 2009-12-30
Sould be able to try it soon. Too many projects!

---

