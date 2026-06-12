---
title: "Sony Laptop Suspend"
date: 2011-07-24
forum: General Help
---

### Post by lakerssuperman on 2011-07-24
I have a Sony VPCCW17FX laptop.  When I close the lid or hit suspend it seems as though it goes into sleep.  The power light blinks and everything looks good.  When I press a key it comes back on but goes back to the opening VAIO screen and boots back to the login screen.  Does anyone have any experience getting suspend to work on this, or a similar machine?

---

### Post by lakerssuperman on 2012-02-20
Just figured I'd give this a bump since it's been awhile without any response.  Everything works on this laptop except for suspend.  It looks like it goes into suspend, but when I try to bring it out it turns back on, but goes right to the bios after rebooting.  I have tried everything up to the 3.2 kernel with this laptop with no success.  I have tried various other distros as well, also with no success.

Are there any generic tips for power management issues I might be able to try to troubleshoot this issue.  Thanks for any help you guys can provide.

---

### Post by lakerssuperman on 2012-02-24
I have found a solution to the problem.

[http://ubuntuforums.org/showthread.php?t=1556934](http://ubuntuforums.org/showthread.php?t=1556934)

Basically, you have to add "acpi_sleep=nonvs" to your Grub configuration to make suspend work.  I have tried multiple suspend cycles and it has worked every time.

---

