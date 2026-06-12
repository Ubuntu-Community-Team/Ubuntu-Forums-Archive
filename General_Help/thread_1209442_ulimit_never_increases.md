---
title: "ulimit never increases"
date: 2009-07-10
forum: General Help
---

### Post by rob_gar_esp on 2009-07-10
Hi,

After setting /etc/security/limits.conf to:
* hard nofile 32768


In /etc/bash.bashrc with:
ulimit -u unlimited


And finally in /etc/pam.d/common-sessions
session required pam_limits.so


I always get:

$ulimit -n
1024

How can I increase the unlimit size?

Thanks!!!

---

