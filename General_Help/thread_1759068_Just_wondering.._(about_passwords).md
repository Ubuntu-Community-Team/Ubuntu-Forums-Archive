---
title: "Just wondering.. (about passwords)"
date: 2011-05-15
forum: General Help
---

### Post by Jordii on 2011-05-15
I was just wondering, why does it take Ubuntu way more time to decline a password than to accept one? For example, in terminal, when I enter the right password it starts working almost immediately, but when I enter a wrong one, it takes a few seconds until the message "Sorry, try again" pops up. Not that It really bothers me, but I'd just like to now why this happens.

---

### Post by Wim Sturkenboom on 2011-05-15
That's to make it a bit more annoying for brute force attacks. Try a pwd, try again, try again, ..., ... . If there are a few seconds in between before a new attempt can be made, the brute force attack will take a lot longer.

---

