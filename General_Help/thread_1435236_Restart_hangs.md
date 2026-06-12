---
title: "Restart hangs"
date: 2010-03-21
forum: General Help
---

### Post by pwhipped on 2010-03-21
I am using Ubuntu 9.10. Every time I try to reboot my system it hangs. Shutdowns work properly. I've done multiple re-installations. Nothing I've tried fixes the problem. Does anyone have any suggestions?

---

### Post by pwhipped on 2010-03-21
Bump

---

### Post by pwhipped on 2010-03-21
Ok... I installed outstanding drivers from system>administration>hardware drivers. The issue appears to be related to the B43 wireless drivers not being activated. In my last ubuntu installation I went weeks without having the restart hang problem. I **think** I recently disabled the wireless drivers as I have no need for them on this computer. This could explain the problem. However, I still don't know why you would need to have them activated to restart properly.

---

### Post by pwhipped on 2010-03-22
I thought the driver activation fixed the problem. This is not the case. I still cannot restart without manually powering down my box. :/ Any help would be greatly appreciated.

---

### Post by pwhipped on 2010-03-22
I found a thread that I had not seen previously. Sudo reboot works and seems to have fixed the problem. I cannot find any problem in my logs, or any reason why doing a simple sudo reboot would fix anything. A shutdown -r +0 didn't work before. I thought reboot was just an alias. Anyone care to comment as to why this would be the case?

---

