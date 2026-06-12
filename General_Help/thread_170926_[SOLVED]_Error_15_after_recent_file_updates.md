---
title: "[SOLVED] Error 15 after recent file updates"
date: 2006-05-05
forum: General Help
---

### Post by pappo on 2006-05-05
Today the update program said I needed to update 69 files.  There were two kernel updates, one for 386 and one for 686, and the rest were all related to new x-server updates.

After I completed the updates, the system recommended a restart. When GRUB tries to start I keep getting "Error 15".

Any ideas on how I recover from this ??

Regards,

Pappo

---

### Post by zxee on 2006-05-05
I'm not at my home computer right now but I think error 15 means file not found. Does your grub give you the option to boot from an older kernel?
I know in both dapper and breezy I have that option. If that doesn't work you might try booting from the install cd and typing 'linux rescue' at the boot prompt. Report back on what the results are and I'm sure someone will try to help you.

---

### Post by pappo on 2006-05-05
I have two kernels but Grub is not going far enough to give me the option of selecting another kernel.  I am going to try using my Ubuntu Live CD to be able to use Grub to try to recover it.
If that doesn't work, I will try the "linux rescue" method.

---

### Post by pappo on 2006-05-05
I fixed it using my Ubuntu Live CD:

1.  Booted up with the Live CD.
2.  Did "apt-get update"
3.  Did "apt-get install grub"
4.  Ran "grub"
5.  At grub >:
       root (hd0,0)
       setup (hd0)   Watched the screen to see that it all completed OK.
6.  Removed the Live CD and rebooted.  It all came back properly.

---

