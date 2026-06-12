---
title: "Force automatic grub selection - how to?"
date: 2009-12-06
forum: General Help
---

### Post by arcull on 2009-12-06
Hi everyone. I did notice on my Ubuntu 9.10, that in some cases after electricity blackout, hardware reboot,... when I start the machine the grub is displayed and it won't automatically select default option after predefined timeout, instead it waits until I press enter to continue booting. Now I wonder if there is someway to force the grub to always automatically boot the default option after timeout. Any advice much appreciated, thanks.

---

### Post by lidex on 2009-12-06
Seems odd. Try this. Press key combo Alt+F2 and enter "Startup-Manager" - minus the quotes. Go to the "Advanced" tab and click the "restore original settings" button. Reboot.

---

### Post by sondo2121 on 2010-02-24
I am also having this problem.  It happens randomly and it's on a server where I need it to reboot when I tell it to...I don't want it to 'hang' @ the grub menu.

Does anybody have insight as to force it to boot a specific kernel?

Thanks in advance.

EDIT:  I am running GRUB 2 (Still new to Linux in general, but was fairly familiar with GRUB 1)

---

### Post by meierfra. on 2010-02-25
Have a look at this:
[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)

---

### Post by lidex on 2010-02-25
Haven't used grub2 but his should provide what you need:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

OR

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by sondo2121 on 2010-02-25
> **meierfra. said:**
> Have a look at this:
[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)


Thanks for the info.  I did that and so far (1 boot later) it booted like it should.

---

