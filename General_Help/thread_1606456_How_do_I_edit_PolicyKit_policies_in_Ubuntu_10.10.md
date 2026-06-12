---
title: "How do I edit PolicyKit policies in Ubuntu 10.10?"
date: 2010-10-26
forum: General Help
---

### Post by Vermind on 2010-10-26
Hi,
I can't seem to find the "Authorizations" GUI that was present in earlier ubuntus for configuring system policies. It used to be in System - Administration - Authorizations. Which package does it come in? What's the console command for it? Thanks.

---

### Post by sisco311 on 2010-10-26
The GUI editor was problematic and it was removed from the new policykit (since 9.10 if memory serves). 

Now you have to create .pkla files manually in /etc/polkit-1/localauthority/50-local.d/ (I think that's the proper location). 

See:
```
man pklocalauthority
```
and
[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)

---

### Post by Vermind on 2010-10-27
Thanks, that should be enough for now.

---

