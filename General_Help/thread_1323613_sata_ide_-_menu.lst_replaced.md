---
title: "sata ide - menu.lst replaced"
date: 2009-11-11
forum: General Help
---

### Post by aspergerian on 2009-11-11
My Acer 1410 Solo core prefers sata for Vista and ide for Ubuntu. Delving into bios at each boot is inconvenient. Some Ubuntu lines have been suggested in various forums, but most that I've found refer to placing a line within menu.lst /boot/grub/menu.lst, which has been eliminated or changed in 9.10. 

Suggestions would be appreciated!

---

### Post by bashphoenux on 2009-11-11
arent you able to dual boot?

---

### Post by Mark Phelps on 2009-11-11
If you prefer to have the MBR setup for Vista, you have the alternative of using EasyBCD to add Ubuntu to the Vista OS menu and boot into Ubuntu from there.

Details, as well as the free software for doing this, can be found at the NeoSmart Technology forums under EasyBCD support.

---

### Post by aspergerian on 2009-11-12
I can dual boot, but bios tweak is required. Vista requires sata be set in bios. Ubuntu requires ide be set in bios. There seem to have been some ubuntu or linux workrounds by placing one or more lines in menu.lst (/boot/grub/menu.lst) but menu.lst has been removed from Ubuntu in 9.10. These tweaks allowed a user not to have to reset bios each time when switching from Ubuntu to Vista or vice versa.

The sata/Vista Ubuntu/ide conflict has been known for a while
[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

I tried the fix specified on the above url, but that didn't help. 9.10's removal of menu.lst seems part of the problem, thus I'm seeking more specific workaround instructions.

---

### Post by aspergerian on 2009-11-12
> **Mark Phelps said:**
> If you prefer to have the MBR setup for Vista, you have the alternative of using EasyBCD to add Ubuntu to the Vista OS menu and boot into Ubuntu from there.

Details, as well as the free software for doing this, can be found at the NeoSmart Technology forums under EasyBCD support.

I'll take a look at EasyBCD.

My computer arrived with Vista, so Vista appears first on the HD, and Ubuntu handled that OK. I get one version or another of a grub menu that allows me to select Vista or Ubuntu. However, I have to ensure that the bios setting is correct for either OS. Vista on my Acer 1410 solo core computer wants sata. Ubuntu wants IDE

I don't want to run Ubuntu from within Vista. Initial boot options seem OK, other than the fact that the bios needs be tweaked if I'm switching from one OS to the other.

Here's the fix that no longer applies since menu.lst has been removed and grub changed:

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)
# Open a terminal and enter "sudo gedit /boot/grub/menu.lst"
# Change "# defoptions=quiet splash" to "# defoptions=quiet splash libata.force=noncq"
# Save and close gedit, then run "sudo update-grub" on the command line. 


The replies are appreciated

---

