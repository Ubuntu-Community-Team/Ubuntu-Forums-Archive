---
title: "swat (samba web tool) problem"
date: 2004-10-23
forum: General Help
---

### Post by macsaint on 2004-10-23
Hello.

I tried to use swat, but it was not possible to login as root.
Ubuntu doesn't have the root account.

How can I solve this problem?

Thanks in advance.

Regards,
JW

---

### Post by flygmaskin on 2004-10-23
"sudo passwd root" will let you set a password for the root account. That should do it.

---

### Post by phuocho on 2007-01-27
I tried "sudo passwd root" but still can not log into swat.  I get the following in the auth.log file:

Jan 27 22:52:10 basket swat[7797]: (pam_unix) authentication failure; logname= uid=1000 euid=1000 tty=samba ruser= rhost=0.0.0.0  user=root

Please help.

---

