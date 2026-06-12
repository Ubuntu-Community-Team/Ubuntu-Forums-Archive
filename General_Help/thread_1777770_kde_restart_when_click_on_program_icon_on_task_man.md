---
title: "kde restart when click on program icon on task manager or with alt+tab"
date: 2011-06-08
forum: General Help
---

### Post by avary on 2011-06-08
Hello. I run Ubuntu 10.10, recently I got this problem. if I open more than one program, and click on icon of them on task bar to switch between them, KDE crash and restart with log in screen. now since 2-3 days this restart also happening when I ALT+TAB to switch between running programs . how i can fix this ?  thanks.

---

### Post by Zorael on 2011-06-08
That sounds like a real bug.

Could you attach your **/var/log/kdm.log** and **/var/log/Xorg.0.log.old** files, perhaps?

---

### Post by avary on 2011-06-09
> **Zorael said:**
> That sounds like a real bug.

Could you attach your **/var/log/kdm.log** and **/var/log/Xorg.0.log.old** files, perhaps?

hi, here is the log files
[http://www.rawanyol.com/Xorg.0.log.old.txt](http://www.rawanyol.com/Xorg.0.log.old.txt)
[http://www.rawanyol.com/Xorg.0.log.txt](http://www.rawanyol.com/Xorg.0.log.txt)
[http://www.rawanyol.com/kdm.log.txt](http://www.rawanyol.com/kdm.log.txt)

these are from Xorg.0.log.old
 13350.029] Segmentation fault at address 0x50005 [ 13350.029]  Caught signal 11 (Segmentation fault). Server aborting [ 13350.029]  Please consult the The X.Org Foundation support  	 at [http://wiki.x.org](http://wiki.x.org)

is it caused by ATI drivers?

---

### Post by Zorael on 2011-06-09
```
[ 13612.925] (II) fglrx(0): Shutdown CMMQS
[ 13612.925] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[ 13612.925] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x7394000 at 0xb78a9000
[ 13612.984] (II) fglrx(0): Interrupt handler Shutdown.
```
```
Backtrace:
[ 13350.029] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80ef31b]
[ 13350.029] 1: /usr/bin/X (0x8048000+0x5d00d) [0x80a500d]
[ 13350.029] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x88d40c]
[ 13350.029] Segmentation fault at address 0x50005
[ 13350.029] 
Caught signal 11 (Segmentation fault). Server aborting
```
I'd wager it's the videodriver, yes. The X backtrace is pretty useless though, and I'm not familiar with AMD cards and their drivers. Have you tried the proprietary Catalyst? And is fglrx the same as [xserver-xorg-video-radeon](apt://xserver-xorg-video-radeon)?

That said, you could add the bleeding-edge **xorg-edgers** ppa (**ppa:xorg-edgers/ppa**) and upgrade to the fresh versions of X and drivers available from there. But obviously there are no guarantees with regards to stability. Caveat installer. Downgrading back is pretty easy though with the **ppa-purge** tool.
```
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```

---

### Post by avary on 2011-06-12
hi
i'v upgraded xorg stuff as you said  , and updated ATI drivers to lastest one, but still didn't fix my problem. except i can use alt+tab now .

---

