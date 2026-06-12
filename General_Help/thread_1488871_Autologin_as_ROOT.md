---
title: "Autologin as ROOT"
date: 2010-05-20
forum: General Help
---

### Post by hakermania on 2010-05-20
is possible to have access as root to your system from the login, and not only from the console?
don't tell me about the risks. i know.

---

### Post by John Bean on 2010-05-20
No. In a standard Ubuntu setup the root account is not available to users and has no password - in other words you can't log in as root, automatically or not.

---

### Post by snowpine on 2010-05-20
> **hakermania said:**
> i know.

No you don't; if you did, you wouldn't have asked the question. :)

---

### Post by bodhi.zazen on 2010-05-20
> **hakermania said:**
> is possible to have access as root to your system from the login, and not only from the console?
don't tell me about the risks. i know.

Of course it is possible, a better question is it advisable ?

This behavior is, IMO,  inappropriate and not supported here, see 

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

If you search (google) you shall find. Good luck with that.

If you need a root shell use sudo -i and use gksu for graphical apps.

---

