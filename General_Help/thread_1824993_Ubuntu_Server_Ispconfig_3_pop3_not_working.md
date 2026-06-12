---
title: "Ubuntu Server Ispconfig 3 pop3 not working"
date: 2011-08-14
forum: General Help
---

### Post by gkellison on 2011-08-14
I have a clean install of 64bit Server 11.04 with IspConfig 3 following the The Perfect Server- Ubuntu 11.04 [ISPConfig 3] located here
[http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3) and cannot seem to get my email client evolution to check emails from server. Squirrelmail does go through the login process but then stops with the following error. 

Error opening ../config/default_pref
Could not create initial preference file!
/var/lib/squirrelmail/data/ should be writable by user web2
Please contact your system administrator and report this error.

I assume I get this error because the pop3 is not working properly?

Here is the Ispconfig 3 mail log.

Aug 14 13:14:59 ubuntuserver pop3d: Connection, ip=[::ffff:192.168.0.71]
Aug 14 13:14:59 ubuntuserver pop3d: LOGOUT, ip=[::ffff:192.168.0.71]
Aug 14 13:14:59 ubuntuserver pop3d: Disconnected, ip=[::ffff:192.168.0.71]
Aug 14 13:15:01 ubuntuserver pop3d: Connection, ip=[::ffff:192.168.0.71]
Aug 14 13:15:02 ubuntuserver pop3d: Connection, ip=[::ffff:127.0.0.1]
Aug 14 13:15:02 ubuntuserver pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Aug 14 13:15:02 ubuntuserver imapd: Connection, ip=[::ffff:127.0.0.1]
Aug 14 13:15:02 ubuntuserver imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0

I am a Ubuntu newbie so please excuse me if I am missing something?
Thanks.

---

### Post by fmmarzoa on 2012-05-07
Did you solve this? I am facing similar problem.

---

### Post by gkellison on 2012-05-08
I never did solve the problem. I actually have been using webmin since I never get a response to this post.

---

