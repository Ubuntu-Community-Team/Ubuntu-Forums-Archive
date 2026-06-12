---
title: "Issue with rebooting..."
date: 2009-12-10
forum: General Help
---

### Post by Falkor on 2009-12-10
Hi all,

I am using 9.04 and I am having issue with rebooting.

When I reboot Ubuntu, instead of:

----------------
exit Ubuntu --> system POST --> load Ubuntu
----------------

It will just:

----------------
shut down services --> restart them back right away --> login screen
----------------

I took out the "quiet" option in the menu.lst, but I don't see anything that rings the bell.

The only thing that I did before this issue happens, is that I have compiled and installed a custom kernel. Yet I have still been using the default one (2.6.28-17-server). I actually had this issue before with 8.10, that it just happened all of the sudden.

Anyone else has a similar issue?

---

### Post by Chesamo on 2009-12-10
How are you rebooting? sudo reboot? Or System > Restart?

---

### Post by Falkor on 2009-12-10
Thanks for your reply.

I have tried:
- using "reboot" option from the login screen, or desktop.
- using "reboot" from command line.
- using "shutdown -r now" from command line.

and they are have the same result.

With this issue, let's say I change the default in the menu.lst, from 0 to 1, grub will still boot 0, as the system has not been fully reboot.

I can shutdown the system fine though.

---

### Post by Falkor on 2009-12-10
Besides the custom kernel, I haven't done anything else, and after I compiled and installed the custom kernel, I haven't boot with it once.

Could it be some issue with ACPI? But before compiling the custom kernel, my system could reboot fine.

---

### Post by Chesamo on 2009-12-10
It *may* be an ACPI issue... the ACPI module might be incompatible with your modified kernel (though since it doesn't work even with the standard kernel then I doubt that's it). Hmm... I'm not so sure then.

---

### Post by SkyGlider on 2009-12-10
HI!

im having exactly the same problem (9.04 Jaunty)... built a custom kernel and now i can't reboot... always have to press the reset button...

it's weird because i don't remember touching any of the power-related options in menuconfig

anyone got a clue yet?

---

