---
title: "UPSTART jobs and /etc/default/*  - config files"
date: 2011-02-21
forum: General Help
---

### Post by kapetr on 2011-02-21
Hello,

I had try to add "-l" parameter to **acpid** server, which is run by upstart.

So there is **/etc/default/acpid** (from acpid package) to add such parameters.
But it does nothing. I have search why.

And if I have see at **/etc/init/acpid.conf** then there is **NO** sourcing and use of /etc/default/acpid.

And as I see - by many other jobs it is the same. They do not use its config files in /etc/default

What is wrong ?!

--kapetr

---

### Post by kapetr on 2011-02-25
touch

---

