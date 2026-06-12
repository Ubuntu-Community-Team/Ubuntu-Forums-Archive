---
title: "2 boot loaders - how to remove 1 of them?"
date: 2012-09-05
forum: General Help
---

### Post by sohlinux on 2012-09-05
I installed windows 7 then I installed ubuntu 12.04, then I removed windows 7 and re installed it but now I appear to have 2 boot loaders

when I first turn on the pc it gives me 2 options - choosing linux or windows

if I click windows it goes directly to windows 7

if I click linux it goes to another boot loader which gives me 2 options - windows or linux

so to get to linux I have to go through 2 boot loaders

so the question is how do I remove one of the boot loaders? and which one do I remove?

thanks

---

### Post by dragonfly41 on 2012-09-05
**Grub customizer** might help you. It's a GUI to select what comes up on booting.

Incidentally I had the same in my dual boot when I used EasyBCD in windows which creates a second boot menu.

---

### Post by oldfred on 2012-09-05
This sounds like a wubi install?

The first boot loader is the Windows boot loader and wubi uses the Windows boot loader to load. The grub menu is wubi is just to show the standard menu and can be reduced in time shown or hidden.

Customizer still should work.
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)



[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by sohlinux on 2012-09-05
> **dragonfly41 said:**
> **Grub customizer** might help you. It's a GUI to select what comes up on booting.

Incidentally I had the same in my dual boot when I used EasyBCD in windows which creates a second boot menu.


hhhm now you mention it I remember installing easybcd after I reinstalled windows because I couldnt get back to linux, so the question is, is it safe to completely remove the first boot loader with easybcd so I will get the second boot loader showing first?


quote oldfred, no its not wubi, I have a partition for linux

---

### Post by dino99 on 2012-09-05
let grub-pc as the default bootloader. Purge them all (except the windoz one) then reinstall grub-pc

---

### Post by sohlinux on 2012-09-05
> **dino99 said:**
> let grub-pc as the default bootloader. Purge them all (except the windoz one) then reinstall grub-pc

not sure what you mean purge them all? and you mean to leave easybcd on too?

---

### Post by sohlinux on 2012-09-05
:confused:

---

### Post by dragonfly41 on 2012-09-05
My windows dual boot is down at the moment (failed disk) but my suggestion would be to go back into windows and remove the easybcd boot.

However I would first take the precaution of having **[COLOR=Navy]boot-repair-disk[/COLOR]** burned onto a CD as a standby so you can repair boot if anything goes awry.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sohlinux on 2012-09-06
> **dragonfly41 said:**
> My windows dual boot is down at the moment (failed disk) but my suggestion would be to go back into windows and remove the easybcd boot.

However I would first take the precaution of having **[COLOR=Navy]boot-repair-disk[/COLOR]** burned onto a CD as a standby so you can repair boot if anything goes awry.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

when I removed easybcd it only gave me windows 7 directly, no more options

I did fix the problem in the end, I removed windows 7 from the second boot using ubuntu startup manager then set the time of the boot to zero seconds so I still have 2 boots but it acts like one.

---

