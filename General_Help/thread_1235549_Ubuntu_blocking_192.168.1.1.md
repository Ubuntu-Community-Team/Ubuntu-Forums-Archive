---
title: "Ubuntu blocking 192.168.1.1"
date: 2009-08-09
forum: General Help
---

### Post by xenogia on 2009-08-09
Hi, it seems Ubuntu is blocking me from going 192.168.1.1 in my browser.  I tried it on my other laptop and I can login fine.  I have ufw disabled, any ideas?

---

### Post by Monicker on 2009-08-09
What do you mean by "blocked"?  Do you get an error page, blank page, etc?  If 192.168.1.1 is a router or some such, does it have logs showing that it even sees the connection attempts?

---

### Post by xenogia on 2009-08-09
> **Monicker said:**
> What do you mean by "blocked"?  Do you get an error page, blank page, etc?  If 192.168.1.1 is a router or some such, does it have logs showing that it even sees the connection attempts?
Well I get the following message on the screen after it sits there.  

"TCP Communication Error"

This doesn't happen on my trust little eeePC which is also running Ubuntu 9.04

 As for logs I cannot check at this current time on the router.

---

### Post by Monicker on 2009-08-10
Start with some basic network troubleshooting.  Can you ping the address from the problem computer?  Can you telnet to port 80 and get a response?  Have tried a different browser?

---

### Post by xenogia on 2009-08-11
Well I figured out after several days it was actually Firefox that was causing the issue.  For some bizarre reason it was blocking it.  I just uninstalled Firefox including all the settings in the /home directory and reinstalled it.  And everything is now working fine.

---

