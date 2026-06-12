---
title: "Adding a group using usermod - how?"
date: 2010-11-29
forum: General Help
---

### Post by zozza on 2010-11-29
How do I add myself to a group?

I type groups and get:

zozza adm dialout cdrom plugdev lpadmin admin sambashare

I want to add netdev.

I type:

sudo usermod -a -G netdev zozza 

But when I type groups netdev is not added.

How can I add it?

Thanks.

---

### Post by WorMzy on 2010-11-29
Changes to groups will not take effect until you log out and log back in.

---

