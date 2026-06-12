---
title: "limiting access to home directory"
date: 2010-11-22
forum: General Help
---

### Post by fantastic on 2010-11-22
How can I provide SSH access to a user but limit them only to the home directory? *or how do I prevent them from poking around into configuration files, logs, and web directories?*

---

### Post by dcstar on 2010-11-23
> **fantastic said:**
> How can I provide SSH access to a user but limit them only to the home directory? *or how do I prevent them from poking around into configuration files, logs, and web directories?*

Users **only** have write access into their own /home folder.

---

### Post by fantastic on 2010-11-23
> **dcstar said:**
> Users **only** have write access into their own /home folder.

I understand that. I want to prevent the user from viewing files not in their home drive though, or just limiting them to only their home drive (meaning not letting them change to a directory which is not in their home drive)

---

