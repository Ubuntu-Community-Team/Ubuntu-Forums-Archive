---
title: "command"
date: 2010-07-12
forum: General Help
---

### Post by Richard1 on 2010-07-12
In fedora,  is SUDO a default command?

---

### Post by isecore on 2010-07-12
I believe Fedora goes the traditional route of having a root-user rather than relying on sudo. But I haven't fiddled around with Fedora in a while, so my memory might be in error.

---

### Post by dragos240 on 2010-07-12
Fedora uses su, not sudo. To use su as you would use sudo do this:
su -c "command args"

However, enter root's password, not yours.

---

