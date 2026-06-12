---
title: "increasing file descriptor limit in /etc/security/limits.d"
date: 2011-06-17
forum: General Help
---

### Post by Skaperen on 2011-06-17
I need for certain processes to go above the currently default file descriptor limit, which is 1024 for both hard and soft limit (so an end user cannot just use the ulimit command in bash to raise the limit).  So I tried to set these changes in /etc/security/limits.d to increase the soft limit (by a small amount) and the hard limit (by a large amount).  I added these lines to /etc/security/limits.d ...
```
phil        soft    nofile        2048
phil        hard    nofile        16384

root        soft    nofile        4096
root        hard    nofile        131072
```... and logged via ssh.  But the effect is not seen and ulimit reports the limits still at 1024 and 1024.  Is this being limited because sshd itself, running as root, already has a limit of 1024?  Would a reboot get the change to really be activated?

UPDATE: I finally got a reboot opportunity and make this setting on that server.  It worked for root, but not for the non-root user.

---

