---
title: "posix capabilities problem"
date: 2012-03-09
forum: General Help
---

### Post by genbu on 2012-03-09
Hello all,

I'm trying grant a user the CAP_SYS_RESOURCE posix capability on an Ubuntu 10.04 machine.  I need this so that a process run by this user can write to /proc/self/oom_adj (yes I realize this this is deprecated but I'm going to be stuck on kernel 2.6.32 for a while).

I've installed libcap2 and libcap2-bin.  I've granted the user the cap_sys_resource capability in /etc/security/capability.conf and I've verified that pam_cap.so is loaded via pam but I'm still unable to lower my oom_adj score.  I've re-initiated sessions after any change to this file and I have even rebooted.

```
$ cat /proc/$$/oom_adj
0
$ echo -1 > /proc/$$/oom_adj
-bash: echo: write error: Permission denied
$ echo 1 > /proc/$$/oom_adj
$ cat /proc/$$/oom_adj
1

```

```
$ egrep -v "^#" /etc/security/capability.conf 

cap_sys_resource delete



none *

```
(yes the username is delete)

Am I missing something here?  Am I doing something obviously wrong?  Any pointers are appreciated.

Thanks!

---

