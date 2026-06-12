---
title: "Cyrus login stopped working"
date: 2009-10-02
forum: General Help
---

### Post by tim5901 on 2009-10-02
I have been running the Cyrus Imap server for more than a year now without any problems.
All of a sudden I could not log into my mailbox.  It said the password was invalid.  I haven't changed anything except for the regular updates from the update manager.  I am running 9.04.  

I tried accessing cyradm but received the same password error.  

I used saslpasswd2 to change the passwords but still the same error.  

I deleted the sasl database (/etc/sasldb2) and created the passwords again, but still the same error.

I removed (completely) all the cyrus packages and re-installed them, but still the same error.

I don't want to remove sasl because that will remove a BUNCH of other packages that I don't want to remove.

Help?

---

### Post by tim5901 on 2009-10-09
Well I found the problem.

/etc/default/saslauthd had the PWDIR set as "/var/spool/postfix/var/run/saslauthd".

I changed this to point to "/var/run/saslauthd" and now everything works.

So why did it change?????

Who knows.

---

