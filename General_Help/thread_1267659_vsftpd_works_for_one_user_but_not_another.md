---
title: "vsftpd works for one user but not another"
date: 2009-09-16
forum: General Help
---

### Post by yelirekim on 2009-09-16
I set up vsftpd on an 8.04 box and it works fine for one of the system users, but not another.  It also works for any newly created users, just not this one specific user.  I've tried resetting the password a few times already.

Both are added to the /etc/vsftpd.user_list file, both have identically constructed home directories and identical entries in /etc/passwd.

The specific problem that occurs is as follows:

I establish a connection to the server and it asks for a username, I enter the user name, then it asks for the password, I enter the password and it gives me a "530 login incorrect" even though I've tried SO MANY TIMES.

---

