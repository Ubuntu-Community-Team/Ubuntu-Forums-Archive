---
title: "GRUB 2 only on demand?"
date: 2011-03-14
forum: General Help
---

### Post by Lucas Malor on 2011-03-14
Is there a way to show GRUB 2 interface only if you hold ESC at boot? If I remember well you can do it with GRUB 1.

---

### Post by wilee-nilee on 2011-03-14
> **Lucas Malor said:**
> Is there a way to show GRUB 2 interface only if you hold ESC at boot? If I remember well you can do it with GRUB 1.

You don't mention what distro your running, but try the shift key. It is not due to the type of grub but changed parameters in Ubuntu.

---

### Post by lithopsian on 2011-03-14
Yes.  Edit /etc/default/grub.  The comments should tell you everything you need.  Set the hidden timeout to 0.  The key to hold down is shift.  That should do it for you.

---

### Post by Lucas Malor on 2011-03-15
Thank you. PS: distro updated in my profile

---

