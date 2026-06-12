---
title: "FTP access not working"
date: 2009-07-08
forum: General Help
---

### Post by matt082606 on 2009-07-08
I am tired of beating my head against the wall so I will ask...NO...BEG for help.

I installed proftpd and I am able to connect via my super user.  However all of the new users I create fail to login.

Here is how I create the users:
groupadd group
useradd -s /bin/false -d /home/username -m -g group username

Here is how I set the Password:
passwd username
[then I enter it twice]

And here is what I get from FTP Log:
Command:	USER username
Response:	331 Password required for username
Command:	PASS ********
Response:	530 Login incorrect.
Error:		Could not connect to server

I have checked /etc/passwd and the users are there.

---

### Post by matt082606 on 2009-07-08
I am using Ubuntu Server 9.04

installed proftpd from latest repository over the weekend

---

### Post by matt082606 on 2009-07-08
I fixed it.   had to fix /bin/bash to /bin/false

---

