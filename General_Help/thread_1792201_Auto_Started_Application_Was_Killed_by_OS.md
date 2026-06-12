---
title: "Auto Started Application Was Killed by OS"
date: 2011-06-27
forum: General Help
---

### Post by djsg on 2011-06-27
Hi,

I want to use myscript.sh to auto-start an application. I put myscript.sh into /etc/init.d/ and run "update-rc.d myscript.sh defaults". After reboot, I can see my application was started (its log file was updated), but I cannot see my application running if I do ps -ef. I suspect it is killed by the OS.

Can someone help?

---

### Post by pqwoerituytrueiwoq on 2011-06-27
what is in the script it may have finished or exited in error

---

### Post by djsg on 2011-06-28
the script works well if I run it after login.

---

### Post by djsg on 2011-06-28
Hi,

I've found what causes the problem. My app tries to run in daemon mode. If I want to auto-run it, I need to disable the daemon mode.

---

### Post by jwbrase on 2011-06-28
> **djsg said:**
> the script works well if I run it after login.

But what does it do? What application are you trying to run, and what exact setup is the script doing? Could you post the script here? It's difficult to help with code that isn't behaving as expected when you can't see the code.

EDIT: Ninja'ed

---

