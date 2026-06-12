---
title: "boots to ubuntu after sleeping?"
date: 2011-12-15
forum: General Help
---

### Post by NERJ on 2011-12-15
I have an ubuntu install (latest version) on my main drive, and windows vista on another drive.
I was running some code over night in windows, only to find the ubuntu log in screen the next morning.
Why does it boot to ubuntu after sleeping? 

And why would this be the default setting, because its frankly ridiculous, and I lost that work because of it.

---

### Post by lisati on 2011-12-15
The only time I remember seeing anything quite like this is when I've left my Windows installation running something overnight, such as video rendering, and Windows, in its wisdom, has decided to apply some system updates and restart my machine.

No doubt someone will eventually pop in with other possibilities.

---

### Post by 2F4U on 2011-12-15
> Why does it boot to ubuntu after sleeping? 

Most likely because Windows had to reboot the machine and grub has been configured to boot Ubuntu first.

> And why would this be the default setting, because its frankly ridiculous, and I lost that work because of it.

Most likely because you didn't change the boot order.

---

### Post by NERJ on 2011-12-15
> **2F4U said:**
> Most likely because Windows had to reboot the machine and grub has been configured to boot Ubuntu first.

Most likely because you didn't change the boot order.

Would windows seriously decided to reboot in the middle of a process?

---

### Post by holycow131415 on 2011-12-15
> **NERJ said:**
> Would windows seriously decided to reboot in the middle of a process?
 
Yes. It auto reboots without user intervention after updates if you did not change the default settings for Windows Update.

---

