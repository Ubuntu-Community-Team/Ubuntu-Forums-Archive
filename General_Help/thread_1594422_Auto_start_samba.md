---
title: "Auto start samba"
date: 2010-10-12
forum: General Help
---

### Post by kooldino on 2010-10-12
How do I automatically start the samba server at startup rather than starting it manually?

---

### Post by TheAnachron on 2010-10-12
Should be automatically started by default. 
Make sure you are in the sambashare group so you can use this service.

---

### Post by kooldino on 2010-10-12
It's not auto started.  The service is stopped when I check it.

---

### Post by pricetech on 2010-10-12
How did you configure Samba ??  Did you use the GUI tool or edit the configuration file manually ??

---

### Post by kooldino on 2010-10-12
Probably a little bit of both.

---

### Post by kooldino on 2010-10-14
bump

---

### Post by scrooge_74 on 2010-10-14
so you reboot and samba dosent work?

---

### Post by kooldino on 2010-10-14
> **scrooge_74 said:**
> so you reboot and samba dosent work?

Correct.  I have to manually start the service and then all is well.

---

### Post by luvshines on 2010-10-14
Do you have this file ?
/etc/init/smbd.conf

---

### Post by kooldino on 2010-10-14
Ah, thanks for pointing me in the right direction.  Got it sorted.

---

### Post by 25 minutes on 2012-05-18
How did u solve it. I have same problem

---

