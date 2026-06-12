---
title: "Possible to use Chameleon bootloader instead of GRUB2?"
date: 2010-06-03
forum: General Help
---

### Post by mrinehart93 on 2010-06-03
Awhile back, I made my desktop a hackintosh. The only way to boot it was Chameleon, which I was totally fine with because it looked nice. Currently, I removed OS X, and now only have Windows 7 and Ubuntu (10.04) installed. My gripe is that GRUB2 looks butt-ugly... it's still the basic white-text on black-background, without any graphics or anything. Is it possible to remove GRUB2 and replace it with Chameleon? Or maybe can Ubuntu start using Chameleon as the bootloader in future releases? Thanks!

-Mike

---

### Post by elliotn on 2010-06-03
Well grub can be customized, u can change the text and background, the whole look can be changed

---

### Post by mrinehart93 on 2010-06-04
Even GRUB2? Because I used to be able to customize GRUB before it switched to GRUB2. Now I have no idea how to even start customizing GRUB2 since it seems no one knows what is safe to edit and what isn't.

---

### Post by philinux on 2010-06-04
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming)

---

### Post by srs5694 on 2010-06-04
AFAIK, Chameleon can't directly load a Linux kernel, so at best, you could configure it to chain-load GRUB or LILO, which will then load Linux. In theory, you could do this and manage it all from Linux, although you might need a FAT or HFS+ partition on which Chameleon would store its configuration files. (I actually used HFS+ for a Linux /boot partition for a while, so you could try this if you're adventurous.)

IMHO, though, it's better to stick with Linux-native solutions. My own view is that, unless something is dreadfully wrong with your configuration, you only see a boot loader for a few seconds a day. That's not worth expending much effort to correct a purely aesthetic issue. That said, beyond the theming suggestions, you could look into [BURG,](http://code.google.com/p/burg/) which as I understand it is a prettier version of GRUB. I've never used BURG, though, so I can't offer specific advice on installing and using it. I don't happen to see it in my Ubuntu 9.10 APT repository list, so I don't believe it's included with Ubuntu, at least as of 9.10.

---

### Post by mrinehart93 on 2010-06-04
Hmm, I think I'll try BURG. Is there anyway to backup GRUB2 as it is currently, or is there a way to reinstall GRUB2 incase **** hits the fan?

---

### Post by srs5694 on 2010-06-04
You can back up all the configuration files in /boot/grub by copying them or creating a tarball via tar. An Ubuntu live CD or [Super GRUB Disk](http://www.supergrubdisk.org/) should enable re-installation of GRUB if something goes wrong. I haven't checked the latest Super GRUB Disk to be sure it supports GRUB 2, though, so you should check that to be sure it will work before you rely on it.

---

