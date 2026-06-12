---
title: "Ubuntu 9.10 Remote Desktop Help Needed"
date: 2010-07-26
forum: General Help
---

### Post by predator17m on 2010-07-26
Hi.
I need to increase the ulimit -n limit for users account.I can change it from root account but it's not working for them(bash: ulimit: open files: cannot modify limit: Operation not permitted)
Is anyone who can help me?
Thank you in advance,

---

### Post by anglican on 2010-07-26
> **predator17m said:**
> Hi.
I need to increase the ulimit -n limit for users account.I can change it from root account but it's not working for them(bash: ulimit: open files: cannot modify limit: Operation not permitted)
Is anyone who can help me?
Thank you in advance,
You can't set the ulimit from the shell "ulimit -Sn" or "ulimit -Hn" just reports values. To change them I'd add lines to /etc/security/limits.conf e.g.:

```
username    soft    nofile  2048
username    hard    nofile  2048

```H

---

