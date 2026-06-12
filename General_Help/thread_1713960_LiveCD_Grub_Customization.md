---
title: "LiveCD Grub Customization"
date: 2011-03-24
forum: General Help
---

### Post by Happy Frog on 2011-03-24
After much searching I've found no useful information so hopefully someone here knows how to customize grub2 menus on the livecd.

I can change the splash image, the text, kernel parameters, everything ... except ... the text color.

I've changed the stdmenu.cfg in isolinux of the source, I've changed it in the gfxboot, I've changed every occurrence of color everywhere I find it but it always gets changed back to the original. I'm using UCK and I've read through the scripts but have found nothing.

So I have a fully customized distribution, I've changed everything from the skel to the kernel, with one exception - the boot menu text color. The source iso is Xubuntu 10.10.

Anybody successfully changed the boot menu color?

---

### Post by Happy Frog on 2011-03-25
Nobody?

I found it, it's in gfxboot.

---

