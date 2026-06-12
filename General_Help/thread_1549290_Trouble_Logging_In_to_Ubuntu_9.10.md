---
title: "Trouble Logging In to Ubuntu 9.10"
date: 2010-08-09
forum: General Help
---

### Post by Harthan on 2010-08-09
Hello folks:

I'd just like to say first that I'm new at working with my own Linux OS (I've previously used it at school) and also new to the forums, so I hope I'm posting this problem in the correct location.

I just set up my laptop for dual-booting (Windows XP and Ubuntu 9.10).  Formatted the hard drive, installed both OS, so on, so on.  Both OS were working just fine before I went into the Windows side to update everything - I had to download SP3, security updates, so on, so on.  When I went over to Ubuntu to do the same, that is, update to 10.04 and get any and all other updates that were available, I could not access Ubuntu.  What happens, specifically, is this: after I input my username and password, I get a succession of four dialog boxes informing me that four images could not be located - lock.png, lock16.png, tux-48.png, and warning.png, all located in /usr/shared/pixmaps.  Immediately after this, the screen goes to black and displays some command line text for about one second, too fast to read.  If there is a way to pause this so I can read it, I can do that and post further on what the message displayed there is.

I've barely done anything to Ubuntu since installing it.  A friend walked me through the installation using his own disc, the OS is on its own partition, and as I said, it's 9.10.  All I've messed with so far was to add Device Manager to Ubuntu so I could check out the drivers for my network controller, which I needed on the Windows side.  The last thing I did in Ubuntu was get Device Manager running.  

I tried to attempt something in recovery mode, but that's all a bit beyond me for the moment, given my experience level here.  I hope someone recognizes the problem, and what I can do to resolve it.

Thanks very much.

---

### Post by dino99 on 2010-08-09
when you select ubuntu into the grub menu, edit the boot line (E) and remove [COLOR="Blue"]quiet splash[/COLOR] to see the verbose booting process, then boot (ctrl+X)

your issue might be due to a driver issue (see what to do after booting, looking at errors logged)

---

