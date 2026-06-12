---
title: "Removing windows"
date: 2009-11-26
forum: General Help
---

### Post by brotell on 2009-11-26
Can I remove windows from my computer using gparted without disturbing Ubuntu 9.10: and if so is there any things I have to do before during or after removal..

I currently dual boot with XP on my desktop and Vista on my laptop if I am successful with the desktop the laptop will be next

Thanks in advance


Terry:KS

---

### Post by dcstar on 2009-11-26
> **brotell said:**
> Can I remove windows from my computer using gparted without disturbing Ubuntu 9.10: and if so is there any things I have to do before during or after removal..


Probably, but **[B]if**[/B] you have installed the Grub boot loader on the Windows partition and then delete the Windows partition, then your system will no longer boot and you will have to manually reinstall Grub off a Live CD.

---

