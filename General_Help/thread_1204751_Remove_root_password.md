---
title: "Remove root password"
date: 2009-07-05
forum: General Help
---

### Post by hardyfan on 2009-07-05
I have created a password for root in Jaunty.  I want to undo this silly mistake.  Do I just delete all characters after root in etc/shadow or is there more to it ?  Are there hidden hazards ?

Thanks
Hardyfan

---

### Post by credobyte on 2009-07-05
```
sudo passwd -l root
```

---

### Post by hardyfan on 2009-07-05
Thank you, done as easy as that.

---

