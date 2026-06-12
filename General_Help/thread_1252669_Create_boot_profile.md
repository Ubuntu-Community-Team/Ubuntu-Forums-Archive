---
title: "Create boot profile?"
date: 2009-08-29
forum: General Help
---

### Post by webaake on 2009-08-29
I'd like to create a boot profile but don't have any boot menu with 'Esc', never have on this machine with any version of Ubuntu. So I have to manually edit /boot/grub/menu.lst in order to add boot parameters.

My questions is; how do I manually add a boot parameter to menu.lst for grub to create a new boot profile? Adding 'profile' to the kernel line like this:
... ro video=vesafb vga=0x311 profile
or
replace 'savedefault' with 'profile'?

---

### Post by jocko on 2009-08-29
> **webaake said:**
> I'd like to create a boot profile but don't have any boot menu with 'Esc', never have on this machine with any version of Ubuntu. So I have to manually edit /boot/grub/menu.lst in order to add boot parameters.

My questions is; how do I manually add a boot parameter to menu.lst for grub to create a new boot profile? Adding 'profile' to the kernel line like this:
... ro video=vesafb vga=0x311 profile
or
replace 'savedefault' with 'profile'?
You shouldn't add the profile option directly to menu.lst, that would result in profiling every boot, which would mean your boots would be much slower. But you can add it, reboot and then remove it. Then just add it to the end of the kernel parameters of your first kernel line...
If you really use grub as boot loader (and not have a wubi install which uses the windows boot loader), you should have access to your boot menu. You just have to press Esc at the moment grub starts to load (directly after the bios post finishes).
If you are not quick enough, you can always edit your menu.lst to make the boot menu appear.
To do this, just find the line in menu.lst that says "#hiddenmenu" and remove the #. You may also need to make sure the menu timeout is set to something more than 0, otherwise you won't be able to see the menu.

---

### Post by webaake on 2009-08-29
Thanks that was just what I was looking for!

By the way, I really do not have the 'Esc' option at boot on this machine. It does appear on another machine so I suspect it has to do with the on-board VGA versus the AGP card I actually use. Haven't resolved it from 7.04 to 9.04 and several versions of kernels, fb drivers and nvidia drivers.

---

