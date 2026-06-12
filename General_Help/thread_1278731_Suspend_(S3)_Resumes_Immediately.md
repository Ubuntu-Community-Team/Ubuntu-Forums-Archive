---
title: "Suspend (S3) Resumes Immediately"
date: 2009-09-29
forum: General Help
---

### Post by Cuco3 on 2009-09-29
Has anyone experienced a problem that when you put the computer to suspend / sleep it resumes immediately?

Also, I noticed that when it does resume, all my open windows are gone / closed. Weird...

I'm using:
Dual Boot WinXP w/ Jaunty completely updated
Intel D845PESV Motherboard
GeForce 7600 GS Video Card
WD 80GB JB Hard Drive
Sony DVD/RW Drive
PS/2 Keyboard and Mouse

BIOS settings are:
Plug n Play OS: YES
Suspend Mode: S3

I've also tried disabling USB and USB Boot through the BIOS with no success.

If I had to guess, it's a device that is sending a Wake-Up event, but I don't know how to check which devices are configured to do that in Ubuntu. Although, it strikes me as strange that all my open programs are now closed when it resumes.

I also did some research. Some people suggest that in the front panel USB connectors in the motherboard you should use +5VSB instead of +5V but my mobo doesn't appear to have an option for that through a jumper or BIOS setting.

I also read something about usbcore.autosuspend=, but configuring that setting varies for each distro and I think for Ubuntu it says you have to recompile the kernel (I'm relatively new to Ubuntu so, even if that was the proper way to do it, I wouldn't do it unless I knew how to).

---

### Post by Cuco3 on 2009-09-30
Has anyone had this problem before and been able to resolve it?

---

### Post by Cuco3 on 2009-09-30
I think it might have something to do with the Ubuntu Power Mgmt using a hybrid of Suspend/Hibernate.

The sympsom are:
1. When the computer resumes, it doesn't resume immediately; it shows the Ubuntu startup loading screen as if it resuming from Hibernate.
2. All my programs are closed /missing when it does, which probably means it didn't have enough space to write to the swap file.
3. I read that people where having the same problem resuming from hibernate when their swap file wasn't big enough.

---

