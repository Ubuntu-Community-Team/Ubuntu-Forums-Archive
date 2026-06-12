---
title: "Can't wake up from hibernate"
date: 2009-07-20
forum: General Help
---

### Post by xxxxme on 2009-07-20
After updating all packages yesterday, my laptop doesn't wake up from hibernate.  Before the updates, hibernate worked fine.  What happens: I click gnome menu > System > Shutdown... > Hibernate.  The laptop appears to hibernate and turns off.  When I turn it back on, it boots, showing several errors in the process.  X will not start, the root partition is mounted read-only, and the other partitions that should be mounted are not, but have entries in /etc/mtab.  The only way I have to get back to a "normal" state is booting from a live CD and running fsck on the partitions.

What can I do so hibernate works again?

Ubuntu 9.04
Dell Inspiron 1525

---

### Post by QIII on 2009-07-20
Just to rule out a fairly common problem ...

Have you changed the size of your swap or added more memory since the last time you used the hibernate feature?

---

### Post by xxxxme on 2009-07-22
> **QIII said:**
> Just to rule out a fairly common problem ...

Have you changed the size of your swap or added more memory since the last time you used the hibernate feature?

No, I haven't.

- resumed from hibernate
- connected to Internet and updated
- rebooted
- browsed the Internet
- hibernated
- couldn't resume

---

### Post by xxxxme on 2009-07-27
Any other ideas?

---

### Post by xxxxme on 2009-07-29
Okay, so it looks like that's what happens when I try to hibernate from the gnome menu.  When I hibernate by typing "sudo hibernate" in the terminal, everything is fine.  So how do I get the gnome menu's hibernate to work the same?

---

