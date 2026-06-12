---
title: "Setting up ssh to back up laptop to desktop using deja dup"
date: 2011-11-22
forum: General Help
---

### Post by ken631 on 2011-11-22
the problem the ssh daemon quits in the middle of backup any idea what can be causing this?

---

### Post by salemhouda on 2011-11-22
Add
KeepAlive yes
ClientAliveInterval 60
in /etc/ssh/sshd_config

---

