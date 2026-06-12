---
title: "Why Does The Reboot Command Require Root Privileges?"
date: 2011-11-22
forum: General Help
---

### Post by dniMretsaM on 2011-11-22
Pretty self explanatory. Why does the command [FONT=Courier New]reboot[/FONT] require root privs to run? It strikes me as odd because you can easily shut down the computer if you're not in the sudoers file. Just a curiosity.

---

### Post by papibe on 2011-11-22
I don't know the actual design decision, but I think we inherited the practice from the basic multiuser/multiprocess nature of Linux.

Without it, any process could restart your machine not requiring any interaction with you.

Also, any user (think a server or a workstation providing services) could interrupt the services by rebooting the server.

Just my thoughts,
Regards.

---

### Post by Telengard C64 on 2011-11-22
> **dniMretsaM said:**
> Pretty self explanatory. Why does the command [FONT=Courier New]reboot[/FONT] require root privs to run?

Because it affects the entire system. If you are hosting a number of active users simultaneously you don't want all of them rebooting whenever they feel like it. On a single user system it certainly doesn't matter.

> It strikes me as odd because you can easily shut down the computer if you're not in the sudoers file.

Previous poster was not wrong. IMHO this looks like an accommodation made for the convenience of the desktop environment. I don't know if I'd go so far as to call it a contradiction of separation of privileges, but it is strange in a way.

---

### Post by dniMretsaM on 2011-11-22
> **papibe said:**
> I don't know the actual design decision, but I think we inherited the practice from the basic multiuser/multiprocess nature of Linux.

Without it, any process could restart your machine not requiring any interaction with you.

Also, any user (think a server or a workstation providing services) could interrupt the services by rebooting the server.

Just my thoughts,
Regards.

That's a good point. Thanks.

---

