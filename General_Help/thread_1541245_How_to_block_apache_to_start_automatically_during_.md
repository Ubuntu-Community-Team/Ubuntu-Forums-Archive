---
title: "How to block apache to start automatically during boot time?"
date: 2010-07-28
forum: General Help
---

### Post by csh on 2010-07-28
I am using Ubuntu server 10.04.

After configured apache2 to use HTTPS, apache2 will cause my Ubuntu server to hang during boot time.

I had booted into rescue mode by using Ubuntu server CD. So, anyone, please tell me how to block apache2 from automatically started during boot time?

Please.

---

### Post by quixote on 2010-07-29
If you remove (or rename) apache2 from the /etc/init.d/ directory, apache2 will no longer be able to start.  I realize that's a bit different from what you really want, ie just not start on bootup but still be available as a service.  But that can presumably be fixed once you have your computer working again, and maybe apache2 reinstalled.

---

### Post by csh on 2010-07-31
> **quixote said:**
> If you remove (or rename) apache2 from the /etc/init.d/ directory, apache2 will no longer be able to start.  I realize that's a bit different from what you really want, ie just not start on bootup but still be available as a service.  But that can presumably be fixed once you have your computer working again, and maybe apache2 reinstalled.

No, reinstall apache will not fix the problem. HTTPS access is a must.

---

