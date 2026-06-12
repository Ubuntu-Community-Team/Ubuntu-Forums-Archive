---
title: "Graphics disabled after 12.04 upgrade"
date: 2012-04-26
forum: General Help
---

### Post by hiro24 on 2012-04-26
Hello Ubuntu forums.. has anybody else ran into this??

After doing a do-release-upgrade, my laptop kinda.. hangs at the end of booting.  Graphics never comes up and online.  I have been able to kind of work around it though.  I found that pressing Ctrl-F3 (or any of the others), logging in and typing startx eventually gave me a graphical interface, after killing the current X PID.  I then installed the proprietary ATI drivers and rebooted... same thing.  I now have accelerated X and everything is happy.. except I have no login screen.  Rebooting is still the same situation, I need to log in, kill X and "startx" to get my graphics going.  Xorg.log files show nothing of interest.  This is very annoying. Does anybody have any ideas on what I can check to see about fixing this problem?

---

### Post by pqwoerituytrueiwoq on 2012-04-26
sudo apt-get purge fglrx fglrx-amdcccle
then reinstall fglrx (may want to reboot before doing that)

---

### Post by hiro24 on 2012-04-26
> **pqwoerituytrueiwoq said:**
> sudo apt-get purge fglrx fglrx-amdcccle
then reinstall fglrx (may want to reboot before doing that)

Thanks, but this didn't seem to help.  Same result, no login screen.  I did notice I was wrong, I don't need to kill the x process from command line.  If I just type startx, I'm in unity.  I don't know if it would help but here are the last few lines of my Xorg.0.log when I boot up and it doesn't do anything.

```

[    36.917] (**) ITE8708 CIR transceiver: always reports core events
[    36.917] (**) evdev: ITE8708 CIR transceiver: Device: "/dev/input/event8"
[    36.917] (--) evdev: ITE8708 CIR transceiver: Vendor 0x1283 Product 0
[    36.917] (--) evdev: ITE8708 CIR transceiver: Found keys
[    36.917] (II) evdev: ITE8708 CIR transceiver: Configuring as keyboard
[    36.917] (**) Option "config_info" "udev:/sys/devices/virtual/rc/rc0/input8/event8"
[    36.917] (II) XINPUT: Adding extended input device "ITE8708 CIR transceiver" (type: KEYBOARD, id 18)
[    36.917] (**) Option "xkb_rules" "evdev"
[    36.917] (**) Option "xkb_model" "pc105"
[    36.917] (**) Option "xkb_layout" "us"
[    36.925] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    41.172] (II) evdev: Power Button: Close
[    41.172] (II) UnloadModule: "evdev"
[    41.172] (II) Unloading evdev
[    41.180] (II) evdev: Video Bus: Close
[    41.180] (II) UnloadModule: "evdev"
[    41.180] (II) Unloading evdev
[    41.188] (II) evdev: Power Button: Close
[    41.188] (II) UnloadModule: "evdev"
[    41.188] (II) Unloading evdev
[    41.204] (II) evdev: Sleep Button: Close
[    41.204] (II) UnloadModule: "evdev"
[    41.204] (II) Unloading evdev
[    41.208] (II) evdev: Integrated Webcam: Close
[    41.208] (II) UnloadModule: "evdev"
[    41.208] (II) Unloading evdev
[    41.212] (II) evdev: Logitech USB Receiver: Close
[    41.212] (II) UnloadModule: "evdev"
[    41.212] (II) Unloading evdev
[    41.216] (II) evdev: Logitech USB Receiver: Close
[    41.216] (II) UnloadModule: "evdev"
[    41.216] (II) Unloading evdev
[    41.224] (II) evdev: AT Translated Set 2 keyboard: Close
[    41.224] (II) UnloadModule: "evdev"
[    41.224] (II) Unloading evdev
[    41.232] (II) evdev: PS/2 Mouse: Close
[    41.232] (II) UnloadModule: "evdev"
[    41.232] (II) Unloading evdev
[    41.240] (II) UnloadModule: "synaptics"
[    41.240] (II) Unloading synaptics
[    41.244] (II) evdev: MCE IR Keyboard/Mouse (ite-cir): Close
[    41.244] (II) UnloadModule: "evdev"
[    41.244] (II) Unloading evdev
[    41.248] (II) evdev: Dell WMI hotkeys: Close
[    41.248] (II) UnloadModule: "evdev"
[    41.248] (II) Unloading evdev
[    41.272] (II) evdev: ITE8708 CIR transceiver: Close
[    41.272] (II) UnloadModule: "evdev"
[    41.272] (II) Unloading evdev
[    41.279] (II) fglrx(0): Shutdown CMMQS
[    41.279] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[    41.279] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x2000 at 0x7f983fa42000
[    41.500] (II) fglrx(0): Interrupt handler Shutdown.
[    41.621]  ddxSigGiveUp: Closing log
[    41.621] Server terminated successfully (0). Closing log file.




```

---

### Post by hiro24 on 2012-04-26
It's possible this might be related to the lightdm display manager?  I've included the x-0-greeter log file.  It seems to have a few errors in it but I'm not sure what to make of them.

---

### Post by hiro24 on 2012-04-26
ok, "sort of" fixed the issue.

Installed GDM, ditched LightDM.

Hurray for options! :D

---

