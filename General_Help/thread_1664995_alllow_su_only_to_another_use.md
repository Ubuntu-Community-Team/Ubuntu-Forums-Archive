---
title: "alllow su only to another use"
date: 2011-01-11
forum: General Help
---

### Post by linuxnewbieuser on 2011-01-11
Hello,
i am trying to edit /etc/sudoers to allow a user named "guest" to su to another user named "admin" and that's it.
i added the following line to /etc/sudoers,
guest	ALL = /bin/su admin
but i am still able to su - root from guest. Any suggestions 
Thanks.

---

### Post by lithopsian on 2011-01-11
Which command exactly are you typing that you think should be controlled or prevented by your sudoers file?  Many people are confused by exactly what sudoers does.

To interpret what it happening it would be necessary to see the rest of the sudoers file.  For example, is admin getting su privileges from somewhere else?

---

### Post by linuxnewbieuser on 2011-01-11
i was just hoping to only allow su - root from the user 'guest', so if a user named 'bill' logged in, he wouldn't be
able to su - root but the user 'guest' would be able to. Unless i misunderstood sudo

contents of my sudoers:

root	        ALL=(ALL) ALL
guest	ALL=/bin/su - admin

Thanks,

---

