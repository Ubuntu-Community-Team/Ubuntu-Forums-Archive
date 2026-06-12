---
title: "Boot loader/order"
date: 2010-08-03
forum: General Help
---

### Post by Oxidize on 2010-08-03
How can i edit my boot options in Ubuntu 10.04

---

### Post by Oxidize on 2010-08-03
Anyone??

---

### Post by cj.surrusco on 2010-08-03
What exactly do you want to edit? Do you want to remove entries, change them or add entries?

---

### Post by Mark Phelps on 2010-08-03
> **Oxidize said:**
> How can i edit my boot options in Ubuntu 10.04

Manually, you edit /etc/default/grub -- never, GRUB.CFG!

To use a GUI, install Startup-Manager.  It allows you to change SOME preferences and reruns update-grub automatically for you.

For more complicated stuff, you have to hand-edit the various Custom files. See the link below for details: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

