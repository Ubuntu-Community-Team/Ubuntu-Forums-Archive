---
title: "Boot stalls at different points without error"
date: 2012-06-05
forum: General Help
---

### Post by Falius on 2012-06-05
I use xubuntu through adding the package xubuntu-desktop. When updating the kernel it usually stalls during the reboot but if I load the previous kernel, shutdown and then load with the new one I'd have no trouble after that. Since upgrading to 12.04 it's gotten a lot worse.

Unprompted by any updates the laptop now refuses to load at random intervals. Loading previous kernels doesnt seem to help either. Now, trying to diagnose the problem isnt going so well because it stalls at different points during the boot cycle without any error in the logs. Sometimes it takes up to an hour of power cycling for the boot to complete once. Recovery mode leads to an unresponsive console login screen which wont let me type.

Can anyone help? Is there anything from the logs you'ld like to see?
Thanks to anyone who read to the end.

---

### Post by matt_symes on 2012-06-05
Hi

If it's getting worse and nothing is in the logs then i would *first* check hardware.

1. Check the hard drive. Run SMART. fsck. Check for bad blocks.
2. Check the memory. Run memtest.
3. Check the temperatures of the CPU, board etc.
4. Check for and remove dust or obstructions. Look for short circuts, blown caps etc.
5. Check all cabling is seated correctly.

Run from a LiveCD. Keep rebooting that. Does that freeze ?
Boot into the BIOS and leave that running for 24 hours. Does it  freeze then ?

Does it freeze on any other OS, older distribution ?

If you can swap out some components, such as memory, then do so. Try the hard drive in a different machine. Does it still freeze ?

See if you can pin point a hardware problem.

When your convinced that the problem is not hardware, then look at software. Are the keyboard CAPS lock or other LEDs flashing ? It so then that points to a kernel panic. This may be hardware related.

Can you reboot using the magic key combination ? If so then that points to the kernel (or X) locking up but not crashing (usually).

Kind regards

---

