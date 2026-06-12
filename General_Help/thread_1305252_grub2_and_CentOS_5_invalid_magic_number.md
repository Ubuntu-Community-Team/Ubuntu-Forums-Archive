---
title: "grub2 and CentOS 5 invalid magic number"
date: 2009-10-29
forum: General Help
---

### Post by Giblet5 on 2009-10-29
Karmic - multiboots Win7, XP, Vista, Ubuntu, and CentOS 5.33.

Everything works from the grub boot menu except CentOS. I get an 'invalid magic number' error and CentOS won't boot.

I can't even find out what that error means.

CentOS is running a xen kernel, if that matters.

I want to fix the Ubuntu grub2 config, so if someone can nudge me in the right direction......

---

### Post by Giblet5 on 2009-10-30
bump

---

### Post by Giblet5 on 2009-10-31
To run a multiboot that includes CentOS 5.3, with Ubuntu's grub2 providing the grub updates, it is necessary to reinstall CentOS **[COLOR="DarkRed"]without grub[/COLOR]**.

Then one must boot into Ubuntu and run ```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

That will re-write the appropriate /boot/grub/grub.cfg and the MBR on hd0.

---

