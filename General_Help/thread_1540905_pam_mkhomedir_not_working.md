---
title: "pam_mkhomedir not working"
date: 2010-07-28
forum: General Help
---

### Post by cmervine on 2010-07-28
pam_mkhomedir appears not be be functioning correctly when using LDAP authentication.  When we authenticate a "new" user via LDAP it creates the home folder but does NOT copy the contents of the /etc/skel/ file.   However, if you create a new user via adduser command the contents are copied.

---

