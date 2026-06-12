---
title: "Newbie - Help QT Applications restarting XORG"
date: 2011-03-23
forum: General Help
---

### Post by irishwoody on 2011-03-23
Relative Newbie here.

Ubuntu 10.10
Nvidia 260.19.36 driver (twin video card) One monitor only.

Every time I start some applications Skype, Okular, KeePass, Luckybackup Xorg server crashes and dumps me back at the GUI login screen.

It generates an error in Xorg log file and restarts the xorg server.

After some reading/searching I think the affected applications are all QT applications - not 100% sure though.

Did a little reading re Apport logging to generate a fault report - but this doesn't seem to work or generate a fault as issue seems to be with XOrg related ?

Could anyone provide information on where and how to report my issue, ask for help.

Woody


Backtrace:
[    85.341] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80ef31b]
[    85.341] 1: /usr/bin/X (0x8048000+0x5d00d) [0x80a500d]
[    85.341] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x43d40c]
[    85.341] 3: /usr/bin/X (ProcessWorkQueue+0x30) [0x8079090]
[    85.341] 4: /usr/bin/X (WaitForSomething+0x56) [0x80a4126]
[    85.341] 5: /usr/bin/X (0x8048000+0x26b9e) [0x806eb9e]
[    85.341] 6: /usr/bin/X (0x8048000+0x1a5da) [0x80625da]
[    85.341] 7: /lib/libc.so.6 (__libc_start_main+0xe7) [0x126ce7]
[    85.341] 8: /usr/bin/X (0x8048000+0x1a1b1) [0x80621b1]
[    85.341] Segmentation fault at address (nil)
[    85.341] 
Caught signal 11 (Segmentation fault). Server aborting
[    85.341] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)

---

