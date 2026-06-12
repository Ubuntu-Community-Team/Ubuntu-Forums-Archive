---
title: "'su' password entry problems in a terminal"
date: 2009-10-11
forum: General Help
---

### Post by Detroit_Bad_Boy on 2009-10-11
**[SOLVED]**I am encountering a problem in terminal with Kubuntu 9.04. When I enter the code 'su' on the main terminal screen it asks for my password. I input my password and it returns with 'Authentication Failure'. What could be causing this problem?

---

### Post by khughitt on 2009-10-11
Ubuntu doesn't encourage you to log-in as root. If you just want temporary admin rights, you can use "sudo", e.g. "sudo command", or for gui applications "gksudo command". If you really need to login as root you can do "sudo su -".

---

### Post by Vunutus on 2009-10-11
I believe this is the correct behavior on a standard Ubuntu system. "su" with no arguments attempts to switch to the root user, which is disabled by default in Ubuntu in favor of sudo.

EDIT: Standard Ubuntu system, not standard Linux system =)

---

### Post by m_duck on 2009-10-11
The root account is locked by default in *buntu. Clicky for more info -> [Ubuntu Community Docs - Root Sudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lindsay7 on 2009-10-11
try sudo

---

