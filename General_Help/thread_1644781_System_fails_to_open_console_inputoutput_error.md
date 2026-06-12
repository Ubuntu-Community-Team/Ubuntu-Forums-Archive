---
title: "System fails to open console: input/output error"
date: 2010-12-13
forum: General Help
---

### Post by shaveyourlife on 2010-12-13
Hi all,

I am having a bit of a problem with my system.  When I power up the computer, after going through a grub stage, my system boots up Ubuntu in terminal mode (rather than desktop mode).  No matter what I try to do, I cannot seem to get it to load the graphical mode.  I have tried booting in recovery mode, and fixing broken packages.  I have tried booting in the basic graphic mode or whatever it is called, and nothing seems to work.

When I am in the terminal if I hit CTRL+ALT+F7 to try and bring up the GUI, I get the following errors
```

usb_id[895]: unable to access '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input8/event8'

usb_id[896]: unable to access '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input8/mouse2'

usb_id[899]: unable to access '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input8/event8'

fsck from util-linux-ng 2.17.2
/dev/loop0: clean, 31297/1073152 files, 2374586/4286464 blocks
init: Failed to open system console: Input/Output error
* starting bluemon
disabling in /etc/default/bluemon
* speech-dispatcher configured for user sessions
* starting bluetooth SynCE service... dund
* starting commong Unix printing system: cupsd
```

I did just install some new bluetooth packages in an attempt to get some code that I have working in Linux.  It works in Windows, and I am trying to port it over.  Any suggestions?

Thanks,

jarvis

---

