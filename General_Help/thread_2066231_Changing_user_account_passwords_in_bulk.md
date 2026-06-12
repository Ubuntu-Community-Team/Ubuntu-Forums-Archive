---
title: "Changing user account passwords in bulk?"
date: 2012-10-04
forum: General Help
---

### Post by karthick87 on 2012-10-04
We are supposed to change all useraccount passwords. We have set same username and password for all the 300 systems. We are supposed to change user passwords for every 15 days. Doing it manually eats more time and man power. I hope there is some way to do this via scripting either by bash or tcl. Is is possible? If yes can someone help me pls?

---

### Post by karthick87 on 2012-10-05
Bump for a move..

---

### Post by Mark Phelps on 2012-10-05
Don't know anything about your systems, but changing user passwords every 15 days is ludicrous!  Even every 30 days poses a lot of trouble for folks trying to remember passwords -- even if they are allowed to create their own.

---

### Post by Cheesemill on 2012-10-05
Password hashes are stored in the /etc/shadow file.

Finding a way of syncing this file between all of your machines may be the way to do this.

---

### Post by Lars Noodén on 2012-10-05
What about running Kerberos on a pair of machines to manage the passwords?  Then any changes would only need to happen in one place.

---

