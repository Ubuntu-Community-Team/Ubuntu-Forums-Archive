---
title: "Got Precise Working (Almost Perfect); weird kernel boot parameters"
date: 2012-05-29
forum: General Help
---

### Post by user1397 on 2012-05-29
So when I try booting 12.04 normally, I get a totally black screen after the grub menu, and my wireless does not turn on.

When I pass the acpi=off param to the kernel boot line in grub, I am able to normally boot into ubuntu, but my wireless still will not budge (hardware switch turned off).

When I pass acpi=force however, I get a normal boot and wireless out of the box.  But, standby still doesn't work properly.  I am able to set it to standby using the function+f3 keys just fine, but when I try to come back from standby it gives me the same blank screen as if from the first scenario (booting with no parameters, aka default boot).

If I could just get the standby working fine I would be ecstatic.

Oh and by the way I have a Gateway NV59C09u laptop with default ubuntu 12.04 unity, an intel core i3 proc, 4gb ram, and integrated intel graphics (intel graphics media accelerator HD).

Any thoughts?

EDIT: Found that the parameter acpi_backlight=vendor fixed everything.

For future reference if anyone else comes across this issue, here's what you do:

open a terminal and type
```
gksudo gedit /etc/default/grub
```
edit the line: GRUB_CMDLINE_LINUX=""
and make it look like this: GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
save, close, go back to terminal and type 
```
sudo update-grub
```
and you should be good to go.

of course, this only works if you were able to boot into ubuntu at all.  if you couldn't even boot the live session correctly, just boot the live image again, at the first screen press escape, select your language, then press f6 and select acpi=off (this will make it so you can at least install it properly)

---

