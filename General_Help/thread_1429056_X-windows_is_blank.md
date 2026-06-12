---
title: "X-windows is blank"
date: 2010-03-13
forum: General Help
---

### Post by daisho73 on 2010-03-13
I've had some sound problems and read several places of people removing pulseaudio and just using alsa. I removed several packages named with pulseaudio and reinstall anything related to alsa. 

I'm running Linux Mint 8 x64 - Gnome, 2 ATI 4830 video cards, crossfired. 

Ever since the above, I get a black background with a white login box and a grey task bar with only a power button in the lower right with the shutdown, restart, hibernate, etc. options. Once I login, all I get is a small terminal window in the upper left corner.

I've reinstalled the pulseaudio package, although I read LM8 and the latest Ubuntu may not require it, I made an xorg.conf by running xorg -configure. No matter what I try I cannot get X-windows back with the usual colors, background, taskbar, icons - all of it.

Has anyone seen the mode of X-windows I'm describing and if so, what is it missing? I looked in Xorg.0.log and I only see these warnings and errors:

WW usr/shared/fonts/X11/cyrillic doe not exist
WW Open ACPI failed /var/run/acpi.socket - no such file or dir
WW DRI init changed memory map, adjusting...
EE AIGLX error: dlopen of usr/lib/dri/r600_dri.so failed (usr/lib/dri/r600_dri.so)
EE AIGLX: reverting to software rendering

---

### Post by daisho73 on 2010-03-20
My fix for this was to reinstall  Linux Mint 8 from a live CD but NOT to format or re-partition the drives. It restored it.

However, since then, I've learned for ATI card users, there's a file in /etc/ati called amdpcsdb that can become corrupted. The recommendation I read was to cp the amdpcsdb.default file next to it to the name amdpcsdb, then reboot.

---

