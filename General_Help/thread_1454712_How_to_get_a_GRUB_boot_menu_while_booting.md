---
title: "How to get a GRUB boot menu while booting?"
date: 2010-04-15
forum: General Help
---

### Post by xlrustylx on 2010-04-15
Hi,

I'm relatively new to Linux and I am dual booting Ubuntu 10.04 LTS and Windows XP and I would like to edit my GRUB menu to allow me to choose Windows XP which is on a 2nd hard drive.

But, I can find no menu.lst and there is no GRUB menu while booting up, my computer boots right into Ubuntu.

So, how do I enable the boot menu so that I can edit it and use it?

---

### Post by nixclusive on 2010-04-15
Depress the SHIFT key as you're powering on your computer to reach the grub menu/prompt. You probably need to edit files in /etc/grub.d and run update-grub.

---

### Post by garvinrick4 on 2010-04-15
> **xlrustylx said:**
> Hi,

I'm relatively new to Linux and I am dual booting Ubuntu 10.04 LTS and Windows XP and I would like to edit my GRUB menu to allow me to choose Windows XP which is on a 2nd hard drive.

But, I can find no menu.lst and there is no GRUB menu while booting up, my computer boots right into Ubuntu.

So, how do I enable the boot menu so that I can edit it and use it?
[GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459")

---

### Post by oldfred on 2010-04-15
Ubuntu's sudo update-grub is very good at finding windows and adding it to the menu. When it does not work it usually means there is a problem with windows that may need windows repairs.

To see entire configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

