---
title: "OpenSSH: Mixed authentication methods"
date: 2010-03-04
forum: General Help
---

### Post by yavoh on 2010-03-04
Is it possible to modify sshd_config to require public key authentication for certain users (i.e., no cleartext tunneled passwords) but accept cleartext passwords for other users?

The idea is to require public key authentication for my user account (a sudoer) but allow merely a password for a limited user account (file drop).

---

