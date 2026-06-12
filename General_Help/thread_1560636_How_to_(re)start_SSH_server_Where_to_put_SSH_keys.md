---
title: "How to (re)start SSH server? Where to put SSH keys?"
date: 2010-08-25
forum: General Help
---

### Post by pstein on 2010-08-25
At first I thought that the following command will restart my sshd server:
 
/etc/init.d/sshd restart
 
but there is no "sshd" server in this directory.
 
How else do I (re)start the ssh server?
 
How can I get the version/release number of the sshd server?
 
Where (in which directory) should I put SSH keys?
 
Peter

---

### Post by Charlietje on 2010-08-25
restart the ssh server using:

```
/etc/init.d/ssh restart
```


> Where to put SSH keys?
What do you mean exactly?


You want to log in with a key or with password?

---

