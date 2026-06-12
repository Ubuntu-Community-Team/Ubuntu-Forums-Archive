---
title: "Random sudo permission"
date: 2011-03-14
forum: General Help
---

### Post by Spyderkid on 2011-03-14
when using sudo im not needing to enter passwords? whats going on....?

---

### Post by antaios256 on 2011-03-14
if you have already entered the password in the same terminal that you enter it a second time. however if you close the terminal then open a new one it will require the sudo password again.

---

### Post by doas777 on 2011-03-14
sudo starts a 15 min timer within your shell when invoked. if you use sudo again within that time period (within that shell) it will use your existing authorization.

---

### Post by antaios256 on 2011-03-14
> **doas777 said:**
> sudo starts a 15 min timer within your shell when invoked. if you use sudo again within that time period (within that shell) it will use your existing authorization.


Thanks doas777 for the clarification i wasn't aware of the timer when i replied to the original question.

---

### Post by Spyderkid on 2011-03-15
thanks doas777 i was neither aware of this timer.

---

