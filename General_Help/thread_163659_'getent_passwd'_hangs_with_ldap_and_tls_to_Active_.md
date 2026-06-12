---
title: "'getent passwd' hangs with ldap and tls to Active Directory"
date: 2006-04-21
forum: General Help
---

### Post by jjstautt on 2006-04-21
I have ldap and Kerberos set up to Microsoft Active Directory. Everything works beautifully until I turn on "ssl start_tls" and "tls_checkpeer no" in /etc/libnss_ldap.conf.

When tls is enabled, 'getent passwd' takes 15 minutes to finish. It appears to query Active Directory, returning the users. Then it just hangs for 15 minutes until finally completing. This causes major issues for other programs like useradd when I want to add local users.

I have tried tls, I have tried ldaps, with and without installing my CA's certificate. I have no idea what is causing the problem.

I would like to use ssl so things aren't transferred in plaintext. Has anyone seen this before or does anyone have any suggestions?

Thanks,
Joe.

---

### Post by jjstautt on 2006-05-10
Not a solution, but will work for now:
I set "timeout 2" in /etc/libnss_ldap.conf which causes the hanging connection to timeout. Things seem to work like this, but I get an error in the log every time.

---

