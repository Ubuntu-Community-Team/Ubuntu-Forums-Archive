---
title: "Change ssh shell"
date: 2011-06-15
forum: General Help
---

### Post by hwttdz on 2011-06-15
I'd like to take away ssh privileges for accounts which don't need it (i.e. no incoming to that account).  How can I do this?

---

### Post by hwttdz on 2011-06-20
And the (by which I mean "an") answer is adding either an "AllowUsers" or "AllowGroups" directive to the sshd_config file.  Keeping this down to just the users who should have ssh access should provide some additional level of security.  Looking through log files I see that thousands of attempts are made to ssh into my machine on a weekly basis, most of these come in on the username "root", which isn't an issue since root ssh is disabled by default.  But a large number of them guess common usernames, and I assume guess common passwords, and since I don't know that all my users use strong passwords better to just not give them ssh privileges unless they need them, and in that case to make sure they're using a strong password.  

Apparently on a very large system using pam is a better idea than using the AllowUsers or AllowGroups in the sshd_config.  I did not investigate this in depth.  If someone does later please share.

---

