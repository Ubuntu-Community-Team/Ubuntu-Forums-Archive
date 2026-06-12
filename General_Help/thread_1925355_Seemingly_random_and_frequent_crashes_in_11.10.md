---
title: "Seemingly random and frequent crashes in 11.10"
date: 2012-02-14
forum: General Help
---

### Post by reset042 on 2012-02-14
My desktop computer running Ubuntu Unity has been crashing a lot lately, causing quite a bit of lost work, so I'd be grateful for any help. 

The crashes happen without any warning and go instantly to the black screen of death and thence to the Ubuntu login.

I'm not sure what's causing the crashes but they seem to happen fairly early in a session. In other words, if I can get past the first few minutes the system seems less likely to crash but that might be a subjective and erroneous impression I have.

The two crashes this afternoon caused identical Backtraces in Xorg.0.log.old, which, if theyre any help, are as below:

```
Backtrace:
[ 30483.419] 0: /usr/bin/X (xorg_backtrace+0x37) [0x80a66f7]
[ 30483.419] 1: /usr/bin/X (0x8048000+0x62b3a) [0x80aab3a]
[ 30483.419] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb789a40c]
[ 30483.419] 3: /usr/lib/xorg/modules/extensions/librecord.so (0xb7887000+0x212f) [0xb788912f]
[ 30483.419] 4: /usr/bin/X (_CallCallbacks+0x3c) [0x80769ec]
[ 30483.419] 5: /usr/bin/X (WriteToClient+0x273) [0x80a95a3]
[ 30483.419] 6: /usr/lib/xorg/modules/extensions/libdri2.so (ProcDRI2WaitMSCReply+0x70) [0xb73c5d70]
[ 30483.419] 7: /usr/lib/xorg/modules/extensions/libdri2.so (DRI2WaitMSCComplete+0x73) [0xb73c4003]
[ 30483.419] 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb7357000+0x2453b) [0xb737b53b]
[ 30483.419] 9: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb7357000+0x9233) [0xb7360233]
[ 30483.419] 10: /usr/lib/i386-linux-gnu/libdrm.so.2 (drmHandleEvent+0xce) [0xb73ae9ee]
[ 30483.419] 11: /usr/lib/xorg/modules/drivers/intel_drv.so (0xb7357000+0x9297) [0xb7360297]
[ 30483.419] 12: /usr/bin/X (WakeupHandler+0x53) [0x8076243]
[ 30483.419] 13: /usr/bin/X (WaitForSomething+0x1a5) [0x80a3fa5]
[ 30483.419] 14: /usr/bin/X (0x8048000+0x29ed2) [0x8071ed2]
[ 30483.419] 15: /usr/bin/X (0x8048000+0x1c70c) [0x806470c]
[ 30483.419] 16: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0xb755f113]
[ 30483.419] 17: /usr/bin/X (0x8048000+0x1ca21) [0x8064a21]
[ 30483.419] Segmentation fault at address 0xb5605008
[ 30483.419] 
Caught signal 11 (Segmentation fault). Server aborting
[ 30483.419] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[ 30483.419] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 30483.419] 
[ 30483.452] (II) Power Button: Close
[ 30483.452] (II) UnloadModule: "evdev"
[ 30483.452] (II) Unloading evdev
[ 30483.488] (II) Power Button: Close
[ 30483.488] (II) UnloadModule: "evdev"
[ 30483.488] (II) Unloading evdev
[ 30483.504] (II) MOSART Semi. 2.4G Keyboard Mouse: Close
[ 30483.504] (II) UnloadModule: "evdev"
[ 30483.504] (II) Unloading evdev
[ 30483.508] (II) MOSART Semi. 2.4G Keyboard Mouse: Close
[ 30483.508] (II) UnloadModule: "evdev"
[ 30483.508] (II) Unloading evdev
[ 30483.509] (II) UnloadModule: "wacom"
[ 30483.509] (II) Unloading wacom
[ 30483.509] (II) UnloadModule: "wacom"
[ 30483.509] (II) Unloading wacom
[ 30483.516] (II) UnloadModule: "wacom"
[ 30483.516] (II) Unloading wacom
[ 30483.516] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 30483.579]  ddxSigGiveUp: Closing log
```

---

