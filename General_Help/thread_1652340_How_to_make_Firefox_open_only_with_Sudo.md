---
title: "How to make Firefox open only with Sudo?"
date: 2010-12-24
forum: General Help
---

### Post by Torombolo on 2010-12-24
as the tittle says, need to make firefox access only to in sudo mode, how can i do this?


Thanks in advance.

---

### Post by noah++ on 2010-12-24
It's considered bad security practice to run a program as root unless it's really necessary. Are you trying to restrict Firefox access to a particular user or group of users, or do you have a good reason to run it as root?

If you are trying to restrict who runs it, you should change the executable's filesystem-level ownership and permissions accordingly.

---

### Post by mikewhatever on 2010-12-24
I am with noah++ on that. If you have to ask 'How to make Firefox open only with Sudo?', you most likely never should or need to run it with sudo.

---

