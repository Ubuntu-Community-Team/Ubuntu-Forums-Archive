---
title: "Reboot issue help!!"
date: 2010-12-26
forum: General Help
---

### Post by raw937 on 2010-12-26
I can't reboot - I  get these messages

[B][SIZE=3]init: failed to spawn plymouth main process: unable to execute: no such file or directory
init:failed to spawn hwclock post-stop process: unable to execute: no such file or directory
init:failed to spawn mountall post-stop process: unable to execute: no such file or directory[/SIZE][/B]



WHAT DO I DO TO SAVE MY DATA???

---

### Post by efflandt on 2010-12-26
Some computers do not totally reset properly on reboot.  If you have a computer like that, anytime something tells you to reboot, shut down completely and cold boot instead.  Have you tried shutting down completely and rebooting.

I have one computer that just churns its hard drive doing nothing on reboot.  So it never gets as far as the BIOS splash screen or grub menu.  It initially did that when I installed 64-bit SuSE over 5 years ago (it is an early Athlon64 3200+ 2 GHz).  When I tried Ubuntu, it was able to reboot until some time during updates of 10.04.  So now I have to get back into the habit of shutting down and cold booting.

I had another computer (old P III 550) that would shut down, but not power off automatically unless I used **lapic** kernel boot option.  Although, I don't remember if that affected reboot at all.  I also had to use **acpi=force** (which worked) because otherwise the kernel refused to do acpi with pre-1999 BIOS.

---

