---
title: "Can't boot after kernel update"
date: 2012-09-24
forum: General Help
---

### Post by x1a4 on 2012-09-24
Hi,

I did an update yesterday which included a kernel update.  The new kernel, version 3.2.0-31, doesn't boot.  I just get a black screen.  As a workaround I have to boot to the previous version but I don't want to have to do this every time I boot my laptop.  How can I diagnose what's wrong so I can fix this?  

This is on Xubuntu 11.10.

Thank you.

---

### Post by Bashing-om on 2012-09-24
Could be that the new kernel wiped out your graphics driver. Try this:
Boot to the grub menu, "e'' to edit the boot command line; add "nomodeset" ctl+x to continue to boot//system settings=>drivers ..see if ubuntu can install appropriate graphics driver.

[CENTER]hth <==BDQ
[/CENTER]

---

