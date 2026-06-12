---
title: "Power on SATA device while at desktop, can I get Ubuntu to recognize it?"
date: 2009-12-19
forum: General Help
---

### Post by then00b on 2009-12-19
OK so here's my situation. I have a SATA DVD drive that I power on while in the desktop. However, it doesn't get put in /dev/ or anywhere else, the only way I can get Ubuntu to recognize it is by rebooting the PC with the drive on. However this is annoying because if I'm going to reboot, might as well reboot into Windows where plug and play works for this drive. Is there anyway I can get Ubuntu to "re scan" the SATA bus and look for all devices on it? Because it must do this at some time during the boot process, can I do it again while booted? If so, how?

Thanks.

---

### Post by dcstar on 2009-12-19
> **then00b said:**
> OK so here's my situation. I have a SATA DVD drive that I power on while in the desktop. However, it doesn't get put in /dev/ or anywhere else, the only way I can get Ubuntu to recognize it is by rebooting the PC with the drive on. However this is annoying because if I'm going to reboot, might as well reboot into Windows where plug and play works for this drive. Is there anyway I can get Ubuntu to "re scan" the SATA bus and look for all devices on it? Because it must do this at some time during the boot process, can I do it again while booted? If so, how?

Thanks.

Try the **scsiadd** package.

---

### Post by then00b on 2009-12-20
Thanks, but that didn't work. It either didn't work or I wasn't using it correctly. However, I was able to get Ubuntu to recognize the drive by simply doing dmesg. So either way I got it to work!

---

### Post by dcstar on 2009-12-20
> **then00b said:**
> Thanks, but that didn't work. It either didn't work or I wasn't using it correctly. However, I was able to get Ubuntu to recognize the drive by simply doing dmesg. So either way I got it to work!

dmesg just displays things, so I have no idea how you got it to "do" anything.

---

