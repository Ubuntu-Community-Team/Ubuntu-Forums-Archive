---
title: "Problems with kernel"
date: 2006-05-08
forum: General Help
---

### Post by jsmidt on 2006-05-08
My machine installed kernel 2.6.15-22-686 and the terminal claimed it updated grub.  However my machine still boots up to 2.6.15-20-686.  What do I do?  I need to boot up to 2.6.15-22-686 since I need the headers which only exist for 2.6.15-22-686.

---

### Post by jsmidt on 2006-05-08
I figured out the problem.  I have Ubuntu on one partition and Debian on the other.  The Ubuntu grub menu was being fixed but not Debian's.  The problem is grub was booting from Debian's menu.lst.  How can I get it so when a new kernel comes both menu.lst are updated?

---

