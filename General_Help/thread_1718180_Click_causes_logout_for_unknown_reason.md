---
title: "Click causes logout for unknown reason"
date: 2011-03-30
forum: General Help
---

### Post by styne on 2011-03-30
Hi,

I'm running Ubuntu 10.10. Something really weird keeps happening to me, a total of 3 times so far, and given how it occurs I think I'm going to need help with this one. When I click I all of a sudden get a black screen with some output about states and then the gnome login is displayed.

Here is how it happened:
1) I clicked on the close button on Google Chrome.
2) I double clicked on the Skype icon in the panel.
3) I clicked on a dialog in a Windows 7 Virtual Box guest.

Does anyone have any idea why this is occurring? I doubt you will so how the heck do I go about diagnosing something like this?

This is really annoying because I loose work every time it occurs.


Cheers,

Jason

---

### Post by styne on 2011-03-30
Woah ok make that 4. Now it is unbearable...

Luckily my colleague is a long time linux user and recognised it has something to do with X11.

After looking in the logs I see this:
```
[195624.771] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[195764.363] 
Backtrace:
[195764.445] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[195764.445] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[195764.446] 2: /lib/libpthread.so.0 (0x7f5d8355f000+0xfb40) [0x7f5d8356eb40]
[195764.446] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f5d7ded7000+0x3a3a7c) [0x7f5d7e27aa7c]
[195764.446] 4: /usr/bin/X (FreeClientResources+0xef) [0x44adef]
[195764.446] 5: /usr/bin/X (CloseDownClient+0x5c) [0x43b2ac]
[195764.446] 6: /usr/bin/X (0x400000+0x3fa46) [0x43fa46]
[195764.446] 7: /usr/bin/X (0x400000+0x2187b) [0x42187b]
[195764.446] 8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f5d824cad8e]
[195764.446] 9: /usr/bin/X (0x400000+0x21409) [0x421409]
[195764.446] Segmentation fault at address (nil)
[195764.446] 
Caught signal 11 (Segmentation fault). Server aborting
[195764.446] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[195764.446] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[195764.446] 
[195764.520] (II) Power Button: Close
[195764.520] (II) UnloadModule: "evdev"
[195764.550] (II) Power Button: Close
[195764.550] (II) UnloadModule: "evdev"
[195764.590] (II) Logitech Logitech USB Headset: Close
[195764.590] (II) UnloadModule: "evdev"
[195764.660] (II) CHICONY HP Basic USB Keyboard: Close
[195764.660] (II) UnloadModule: "evdev"
[195764.781] (II) Logitech USB Optical Mouse: Close
[195764.781] (II) UnloadModule: "evdev"
[195764.821] (II) HP WMI hotkeys: Close
[195764.821] (II) UnloadModule: "evdev"
[195765.116]  ddxSigGiveUp: Closing log
```

I see nvidia_drv.so. Does this indicate that it is something wrong with my NVidia driver?

I have attached the full log in case that helps.

---

### Post by styne on 2011-04-03
Woops it seems I had the pre-release and unsupported updates selected in the update options.

Is there anyway that I can revert these packages?

Maybe I should just try out the 11.04 beta...

---

