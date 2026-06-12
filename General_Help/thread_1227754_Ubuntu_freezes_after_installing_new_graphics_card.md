---
title: "Ubuntu freezes after installing new graphics card"
date: 2009-07-31
forum: General Help
---

### Post by dismas on 2009-07-31
I switched from an Nvidia 8300 GS to ATI Radeon 4670. Now when I boot, after the loading bar completes the screen freezes with static everywhere. How can I fix this?

---

### Post by darolu on 2009-07-31
Download the ATI driver; if you don't have another computer or OS installed on the same machine try plugging your Nvidia back in; once you have the ATI driver (download it from amd.com) and the ati card back, boot and choose the recovery mode kernel from the GRUB list (you may need to press Esc to see the list); after that choose console with network (or something like that) you'll reach a console, log in as root; if you don't have root password log in as sudoer user (your main account) and install the video driver you downloaded; you simply run with:
```
~$sh ./youratidriverfile.run
```
if you are not root run with sudo. This should solve it, you can use elinks or links (install with apt-get install links) to browse the web for help while in command-line mode.
Good luck.

---

