---
title: "Touchscreen and stylus stopped working after upgrade to 11.10"
date: 2011-10-16
forum: General Help
---

### Post by luisito on 2011-10-16
I've just upgraded to 11.10 and I got the unpleasant surprise that my touchscreen and stylus do not work any more. They were working fine on Natty with the wacom driver.

I have a Lenovo X201 Tablet. These are the relevant lines on my xorg.0.log
```

[    27.655] (II) Module wacom: vendor="X.Org Foundation"
[    27.655]    compiled for 1.10.4, module version = 0.11.0
[    27.655]    Module class: X.Org XInput Driver
[    27.655]    ABI class: X.Org XInput driver, version 12.3
[    27.655] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    27.655] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    27.655] (**) Serial Wacom Tablet: always reports core events
[    27.655] (**) Option "Device" "/dev/ttyS4"
[    27.662] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    27.662] (II) Serial Wacom Tablet: other types will be automatically added.
[    27.662] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    27.662] (WW) Serial Wacom Tablet stylus: Query failed with 38400 baud. Trying 19200.
[    27.662] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    27.662] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    27.662] (II) Serial Wacom Tablet stylus: serial tablet id 0xE3.
[    27.662] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    27.662] (II) UnloadModule: "wacom"
[    27.662] (II) Unloading wacom
[    27.663] (II) config/udev: Adding input device Wacom Serial Touchscreen (/dev/input/event6)
[    27.663] (**) Wacom Serial Touchscreen: Applying InputClass "evdev tablet catchall"
[    27.663] (**) Wacom Serial Touchscreen: Applying InputClass "Wacom class"
[    27.663] (II) Using input driver 'wacom' for 'Wacom Serial Touchscreen'
[    27.663] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    27.663] (**) Wacom Serial Touchscreen: always reports core events
[    27.663] (**) Option "Device" "/dev/input/event6"
[    27.728] (EE) PreInit returned 8 for "Wacom Serial Touchscreen"
[    27.728] (II) UnloadModule: "wacom"
[    27.728] (II) Unloading wacom

```

---

### Post by druths on 2011-10-19
I can confirm that this error also happens on my Lenovo x201 tablet.  I upgraded from 11.04 to 11.10 via the standard upgrade progress.  Errors are exactly as reported above.  I upgraded xf86-input-wacom to version 0.11.99.  This didn't help anything.

---

### Post by t-c on 2011-10-19
I did the standard dist. upgrade via Update Manager 2/3 days ago to my Toshiba and the touchscreen/stylus worked fine until an update  19/10/2011 unfortunately I didn't take note of the up grade's contents.  I also noticed some intermittent issues between the trackpad and the mouse where the mouse wouldn't work but the trackpad would and then the trackpad buttons would cease functioning then the mouse would work seemed to coincide with the update this morning but unable to verify the root cause as I cannot predict what actions are at play. Is there away to test the service is running I can't identify the process?

---

### Post by Favux on 2011-10-19
Hi,

We're working on the same or similar problem on this thread:  [http://ubuntuforums.org/showthread.php?t=1863935](http://ubuntuforums.org/showthread.php?t=1863935)

---

### Post by luisito on 2011-10-23
It is finally solved!!!

Solution for the impatient: comment out the only line on
/lib/udev/rules.d/40-inputattach.rules 
and reboot.

The problem is worked out in [https://bugs.launchpad.net/ubuntu/+s...ck/+bug/835634](https://bugs.launchpad.net/ubuntu/+s...ck/+bug/835634)
One quick way to check that this solves your problem is killing inputattach and then restarting Xorg. This should have your touchscreen and stylus working again (at least until reboot).

There is also a Debian bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=632961](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=632961)

Apparently that line is necessary to make things work on a Fujitsu laptop, but breaks compatibility with the Lenovo ones.

Incidentally, I used to have a problem with upstart-udev-bridge taking 100% of my cpu that now seems magically solved. Coincidence?

---

### Post by copperhat on 2012-09-22
Thanks, this was a very helpful post.

---

