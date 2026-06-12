---
title: "Problems with vmware xorg driver"
date: 2011-10-18
forum: General Help
---

### Post by ws4100e on 2011-10-18
I've downloaded Ubuntu 11.04 (with VMWare Tools installed) virtual machine from VMware Virtual Appliance Marketplace. The machine started with no problems. Afterwards I rebooted the machine and it started but not with X. 
The info I found in /var/log/Xorg.0.log was:
```

...
[  1703.274] (--) Depth 24 pixmap format is 32 bpp
[  1703.278] (II) vmwlegacy(0): Initialized VMWARE_CTRL extension version 0.2
[  1703.280] (II) vmwlegacy(0): Initialized VMware Xinerama extension.
[  1703.281] (II) vmwlegacy(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[  1703.282] (EE) vmwlegacy(0): Unable to map mmio BAR. No such file or directory (2)
[  1703.409] 
Backtrace:
[  1703.413] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
[  1703.414] 1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
[  1703.414] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x22440c]
[  1703.414] 3: /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so (0x225000+0x4b6e) [0x229b6e]
[  1703.414] 4: /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so (0x225000+0x4cf8) [0x229cf8]
[  1703.414] 5: /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so (0x225000+0x560b) [0x22a60b]
[  1703.415] 6: /usr/bin/X (AddScreen+0x17c) [0x80704ac]
[  1703.415] 7: /usr/bin/X (InitOutput+0x279) [0x80b7729]
[  1703.415] 8: /usr/bin/X (0x8048000+0x1a675) [0x8062675]
[  1703.415] 9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x5bee37]
[  1703.415] 10: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[  1703.416] Segmentation fault at address 0x8
[  1703.416] 
Caught signal 11 (Segmentation fault). Server aborting
[  1703.416] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  1703.417] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1703.417] 
[  1703.510]  ddxSigGiveUp: Closing log
...

```

The problem is (unfortunately) reproducible - it is my third vmachine with Ubuntu 11.04 which suffers it.

Any ideas?

Regards.

Pawel

---

