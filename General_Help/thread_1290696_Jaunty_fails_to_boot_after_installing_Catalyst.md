---
title: "Jaunty fails to boot after installing Catalyst"
date: 2009-10-13
forum: General Help
---

### Post by Rosemachinegun on 2009-10-13
Hi all,
My computer has an ATI Radeon X300 card. It was working perfectly until I installed Catalyst control center to configure it, but it turns out that ATI stopped supporting my card and the driver has crippled my machine. The machine gets to GRUB, and if I select Ubuntu the splash screen comes up, and then when the log-in screen should appear there's simply a black screen.

I tried to fix it by booting from a Live CD, mounting my HD and purging catalyst, fglrx, and its assorted libraries and reinstalling the open drivers(the libgls) but it didn't make any difference.:(

I've tried launching the recovery menu from GRUB to use xfix, but that's no good. For some reason the recovery menu is busted. I can't manipulate it at all, using the arrow keys just results in some useless text appearing on the screen. Sometimes if I type the corresponding word one of the options will be highlighted, but I can't select it.

Any advice would be greatly appreciated.
Thanks for reading.

Edit: I fixed it! After playing around with the broken recovery menu(i.e. mashing keys and hoping for a breakthrough), I somehow got xfix selected. After it ran the menu reappeared and the options were easily selectable. Thereafter I opened up the command-line, purged fglrx and now it's working like a charm. :) Lessons learned: Drivers cannot be altered from the LiveCD; mashing buttons on a broken menu will occasionally save the day.

---

