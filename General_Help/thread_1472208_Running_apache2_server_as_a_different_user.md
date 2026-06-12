---
title: "Running apache2 server as a different user"
date: 2010-05-04
forum: General Help
---

### Post by kevpatts on 2010-05-04
Hey all,

I'm a web developer and I make plug-ins for various shopping cart softwares on demand. because of this I'm constantly installing carts and then immediately updating them/modifying them.

The problem I'm having is that I'm having to update the permissions manually all the time (every time I copy a new cart into the /var/www folder). Instead of doing this I'd like apache2 to run under my user, so I don't ever have to update the permissions again. How do I do this?

Kevpatts

---

### Post by kevpatts on 2010-05-04
Ignore this. I just changed the values in /etc/apache2/envvars and all is working.

---

