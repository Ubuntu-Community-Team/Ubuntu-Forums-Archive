---
title: "Occasionally won't suspend..."
date: 2010-12-29
forum: General Help
---

### Post by TheCosmicFrog on 2010-12-29
Hi guys,

I know there's another thread here on page one regarding a suspend issue, but mine is very different. Back in Ubuntu 10.04 I had no problems with suspend, but in 10.10 every so often (maybe one in five suspend attempts) my laptop will refuse to suspend. 

What happens is, I close my laptop lid, or suspend using the power button on the top taskbar, and the computer will keep chugging along (HDD light keeps blinking) but my screen stays blank. The backlight is still on, however. There is no way to recover my computer from this situation, even using the Alt+REISUB command. The only solution is to hold down my power button and hard-halt my computer.

My output from s2ram is the following:
```

aaron@aaron-notebook:~$ sudo s2ram 
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Micro-Star International"
    sys_product  = "GX620      "
    sys_version  = "Ver 1.000"
    bios_version = "A1651IMS.10V"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.

```Are there any other outputs I can provide that will help in a diagnosis? I'm interested to find out *what exactly* is causing a failed suspend, as it works 80% of the time...

Thanks,
Aaron

---

