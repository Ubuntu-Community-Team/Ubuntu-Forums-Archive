---
title: "Found bug in Dovecot, need help"
date: 2011-07-30
forum: General Help
---

### Post by FrogOmega on 2011-07-30
How can I give an application group permissions?

There is a bug in the latest version of Ubuntu's Dovecot, where it is not apart of mail group, so it does not have write permission to the /var/mail directory by default. So I have to give it mail group permissions.

---

### Post by dino99 on 2011-07-30
report this issue: ubuntu-bug dovecot-common

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

 check that your user is added to mail group

---

