---
title: "Change hostname without restart?"
date: 2010-08-20
forum: General Help
---

### Post by blchinezu on 2010-08-20
As the thread title says: Is there any way to change the hostname **without rebooting** the machine?

As far as I've searched the internet, I've got the solution only for fedora but it's quite different from ubuntu. The rest is the same everywhere:
Change in /etc/hostname and /etc/hosts and reboot but I'd like to avoid the rebooting.

---

### Post by Iowan on 2010-08-20
You might be able to *restart* networking (but the title suggests that's not what you had in mind). Somehow the system needs to re-read some configuration files...

---

### Post by Rubi1200 on 2010-08-20
Just a wild guess, but would logging out and then in again do the trick?

---

