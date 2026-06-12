---
title: "How do you reset a Kerberos password?"
date: 2011-08-05
forum: General Help
---

### Post by Ubuntoheadeache! on 2011-08-05
Hello,

We have an employee that left our place of business on bad terms and his computer has been locked out since. The comp runs Ubuntu 10.10.

We have followed the regular password reset methods online but the Kerberos password seems to be getting in the way. We have no idea was this password is and it seems impossible to work around. Does anybody know a way?

Were were about to gain access as the root user but cannot access other user accounts as the root user. 

HELP!

---

### Post by haqking on 2011-08-05
> **Ubuntoheadeache! said:**
> Hello,

We have an employee that left our place of business on bad terms and his computer has been locked out since. The comp runs Ubuntu 10.10.

We have followed the regular password reset methods online but the Kerberos password seems to be getting in the way. We have no idea was this password is and it seems impossible to work around. Does anybody know a way?

Were were about to gain access as the root user but cannot access other user accounts as the root user. 

HELP!

you need kpasswd to change a kerberos password
[http://manpages.ubuntu.com/manpages/natty/man1/kpasswd.1.html](http://manpages.ubuntu.com/manpages/natty/man1/kpasswd.1.html)

---

