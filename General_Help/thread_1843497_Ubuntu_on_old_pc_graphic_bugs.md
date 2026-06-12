---
title: "Ubuntu on old pc: graphic bugs"
date: 2011-09-13
forum: General Help
---

### Post by tb189 on 2011-09-13
I've tried installing ubuntu 11.04 on 2 old pc's (2003, pentium 4, Dell boxes). The installation goes well, and if I 'try ubuntu' from usb, I get none of the problems below. After installing, however, I only see the default background, and my mouse pointer (not even a menu). Now and then a few flickers of the update manager can be seen. Everything I do (power button, right click, click on places I think the menu is) results in a few flashes of the correct screen before disappearing.

Any idea what the problem is, or where I can start to get more info on where to look?

Thanks!

---

### Post by sanderd17 on 2011-09-13
At the login screen (the point where you have to give your password), can you log in to gnome classic or gnome classic without effects?

---

### Post by tb189 on 2011-09-13
Unfortunately, there is also no login screen. One of the pc's did say the hardware requirements were insufficient to run unity, and reverted to classic (as I saw by the flashes of a top and bottom menu), but the same problems remained. The strange thing is that the live usb worked perfectly ...

---

### Post by mikewhatever on 2011-09-13
You may not get the login screen because you've checked the "Don't ask for password" box during the installation. It's still possible to get back to it by switching to another tty (ctrl-alt-f1), logging in with your username and password, and typing "sudo service gdm restart".

As usually, knowing anything about the graphics would help people help you.

---

### Post by tb189 on 2011-09-13
'sudo service gdm restart' restarts the graphical interface, but doesn't give me a login screen. I'll try re-installing without automatic login. What do you mean by 'knowing anything about the graphics'?

---

### Post by mikewhatever on 2011-09-13
What does restarting gdm give you? Perhaps you have to return to tty7 (ctrl-alt-f7).
In the ideal world, every time someone has a graphics related problem, the output of lspci would be appended to the help request. In my case, that would look as follows:
> ~$ lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
**00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)**
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


In your case, all we have is the obscure '2003, pentium 4, Dell', and can only speculate on what's inside.

---

### Post by tb189 on 2011-09-14
I see. I'll remember that. In any case, re-installing ubuntu with 'require a password to log in' enabled, and selecting ubuntu classic with no effects worked. I don't know what the difference is with the pc that had unity disabled (and still had the problem), but it's gone now.

Thanks for the help!

---

