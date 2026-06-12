---
title: "Boot CD"
date: 2009-10-14
forum: General Help
---

### Post by mike_new_boy on 2009-10-14
I have Ubuntu on one hard disc and windows XP on another. I do not have any dual booting as Windows was installed while the Ubuntu disc was disconnected. At the moment I can boot into either by entering Setup and changing the boot order of the discs.
I would like to make a boot CD. At it simplest I would have Windows on the first disc and the CD would just tell it to boot from Ubuntu on the second disc. Alternatively is it possible to put Grub on a boot CD. 
Does anyone have any ideas as to how I can do it?

---

### Post by P4man on 2009-10-14
why would you want a CD to do that? Would be so slow. Have your machine boot the ubuntu drive by default, and modify your grub menu so it adds windows as boot option. That way you dont risk anything, you can still change the bios boot order to boot windows, and if you dont, you have a convenient menu to select your OS from.

---

### Post by mike_new_boy on 2009-10-14
> **P4man said:**
> why would you want a CD to do that? Would be so slow. Have your machine boot the ubuntu drive by default, and modify your grub menu so it adds windows as boot option. That way you dont risk anything, you can still change the bios boot order to boot windows, and if you dont, you have a convenient menu to select your OS from.

My partner only uses windows and she doesn’t want to have to select it from a boot menu. But I suppose that I could do as you suggest and then set Windows as the default operating system with a short timeout.
I just thought it would be easy to leave it booting to Windows and then I want Ubuntu to put in a CD. If it pointed to Ubuntu on the second disc it would only add a few seconds to the boot time, surely?

---

### Post by P4man on 2009-10-14
> **mike_new_boy said:**
> My partner only uses windows and she doesn’t want to have to select it from a boot menu. But I suppose that I could do as you suggest and then set Windows as the default operating system with a short timeout.
I just thought it would be easy to leave it booting to Windows and then I want Ubuntu to put in a CD. If it pointed to Ubuntu on the second disc it would only add a few seconds to the boot time, surely?

Indeed, I guess it adds about 10s if you include the countdown. I guess it depends how often each OS is booted, but booting grub from a cd would probably add closer to 30s. Then again, putting the cd drive as first boot device will also add a few seconds to every boot;

Anyway, its your choice; personally Id go for grub defaulting to windows to please your significant other ;). other options include using a bios boot menu if you have one. Changing boot priority takes a long time, but most bioses also have a boot menu (F11 on my machine) which is quite fast, and just lets you pick the boot drive. Finally, id use a USB stick rather than a CD if you want an external bootloader.

Anyway, here is the link that explains how to make a grub boot cd. I guess you could put the iso on the USB stick just as well:
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

---

### Post by mike_new_boy on 2009-10-14
Thanks, just what I wanted to know. I tried the boot menu (F9 on my machine) and it is much quicker than setup and will probably use that. If I select the second disc it goes to Grub. I will try a boot CD /USB out of interest but you are probably right it will take longer and not be worth the effort. Thanks again and I can now mark this as solved.

---

### Post by StuartN on 2009-10-14
> **mike_new_boy said:**
> Thanks, just what I wanted to know. I tried the boot menu (F9 on my machine) and it is much quicker than setup and will probably use that. If I select the second disc it goes to Grub. I will try a boot CD /USB out of interest but you are probably right it will take longer and not be worth the effort. Thanks again and I can now mark this as solved.

Why don't you use the Windows boot manager, or something like Partition Magic for Windows if you want pretty. Then you can set up a Windows boot menu with a short time-out that goes to Windows if you do nothing and Ubuntu if you select it.

---

### Post by stinger30au on 2009-10-14
i bet if you use super grub disc you can boot from cd and then tell it what hdd to boot from and it will be just fine

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

