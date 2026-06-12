---
title: "Passing nomodeset to kernel command line"
date: 2011-12-28
forum: General Help
---

### Post by whatthefunk on 2011-12-28
Ive got a new motherboard, an ASRock Z68 Pro3.  It works fine but there is a small display problem on startup.  According to [this]("http://www.phoronix.com/scan.php?page=article&item=asrock_z68_pro3&num=4") article, the problem can be solved by passing nomodeset to "the kernel command line so that the Intel kernel mode-setting driver won't be in use."  The full text regarding the fix:

> To workaround the broken display issue, nomodeset can be passed to the kernel command line so that the Intel kernel mode-setting driver won't be in use, and since user-space mode-setting is no longer supported for Intel hardware, it falls back to using the VESA driver. When the system was up with the VESA display driver, the latest xf86-video-intel DDX was built from Git source on 13 July. When using this newer DDX driver than what is found in Ubuntu 11.04, the DVI and HDMI outputs on the ASRock Z68 Pro3 had properly lit up. After that, it is just a matter of pulling in the latest kernel and Mesa for proper OpenGL support. The Ubuntu 11.04 Alpha 2 release was also tested, which had too required updating the xf86-video-intel driver to avoid this display problem.

Im not understanding this too much.  Could somebody describe how to do this please?

---

### Post by plucky on 2011-12-28
> **whatthefunk said:**
> Ive got a new motherboard, an ASRock Z68 Pro3.  It works fine but there is a small display problem on startup.  According to [this]("http://www.phoronix.com/scan.php?page=article&item=asrock_z68_pro3&num=4") article, the problem can be solved by passing nomodeset to "the kernel command line so that the Intel kernel mode-setting driver won't be in use."  The full text regarding the fix:



Im not understanding this too much.  Could somebody describe how to do this please?

Does your system boot to the login page?

If so edit the file /etc/default/grub with ```
gksudo gedit /etc/default/grub
``` and put nomodeset into the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nomodeset"
```

Then run ```
sudo update-grub
``` to update the grub command line.

Good Luck

---

### Post by whatthefunk on 2011-12-28
Excellent.  Worked like a charm.  Thanks plucky.

---

