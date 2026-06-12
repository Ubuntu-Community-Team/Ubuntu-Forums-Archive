---
title: "Thin client unable to login ltsp server"
date: 2011-09-14
forum: General Help
---

### Post by coreyk67 on 2011-09-14
Hello,

I have an ltsp standalone server setup using a separate dhcp server. The thin client loads to the login screen but will not allow any  user accounts to log in. 

i have tried 
sudo ltsp-update-image

and

sudo ltsp-update-sshkeys

I have also looked here ...  /var/log/auth.log  and no login attempts were logged. 

Any advice would be greatly appreciated.

---

### Post by ITJeff on 2012-01-19
Hi
 
I have exactly the same issue, terminal boots to the login screen, enter user name and password.  After a pause I get the message 'response from server. restarting' and the client duly restarts.
 
As with coreyk67 I have tried
 
sudo ltsp-update-image

and

sudo ltsp-update-sshkeys
 
and
 
/var/log/auth.log 
 
has not indication of an attempt to login
 
I am using edubuntu 11.10
 
Any thoughts plaese.

---

### Post by LEdesigns on 2012-04-17
I am getting the same problem with clients unable to login using edubuntu 11.10  I have no problems with Edubuntu 11.04

---

