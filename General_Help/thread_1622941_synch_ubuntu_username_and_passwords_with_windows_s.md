---
title: "synch ubuntu username and passwords with windows server 2008"
date: 2010-11-16
forum: General Help
---

### Post by james_watt20 on 2010-11-16
Hi!
I have some user on ubuntu server I want to synch the username and passwords on this server with windows server 2008. Users change their password randomly and I want synch server 2008 with the new password. Please help me

---

### Post by deconstrained on 2010-11-16
Try [lastpass](https://lastpass.com/) with different passwords on each machine instead of trying to synchronize them. Your question, while it addresses a rather unorthodox problem, is not uncommonly asked/answered;
[http://superuser.com/questions/25132/password-manager-for-multiple-computers](http://superuser.com/questions/25132/password-manager-for-multiple-computers)
[http://superuser.com/questions/142631/cross-platform-centralized-desktop-password-manager](http://superuser.com/questions/142631/cross-platform-centralized-desktop-password-manager)
Note however that it's not very secure to have similar passwords on multiple machines, especially if some third-party app independent of Windows and Linux is moving them around (which would be necessary).

---

### Post by james_watt20 on 2010-11-16
Thanks for your reply, but I want to synchronize passwords between ubuntu and server 2008. for example when I change my password on ubuntu it is automatically changed on server 2008.

---

### Post by deconstrained on 2010-11-16
Sorry, but the only way to do that is to either give some kind of third-party application (the likes of which I don't even think exist) admin access to both Windows when you change the Linux password and vice versa, or write some kind of script that gets called by pam to hax0r the necessary Windows files and change the password when you change the password in Linux (which would most likely end in disaster). Did you look at any of the suggestions posted in the threads at superuser.com?

---

### Post by deconstrained on 2010-11-17
Another idea: client/server model, i.e. with [Kerberos](http://en.wikipedia.org/wiki/Kerberos_%28protocol%29) on one of the machines. That way there's one password in one place.

---

### Post by james_watt20 on 2010-11-21
what about this:
[http://technet.microsoft.com/en-us/library/bb463208.aspx#EBAA](http://technet.microsoft.com/en-us/library/bb463208.aspx#EBAA)

---

