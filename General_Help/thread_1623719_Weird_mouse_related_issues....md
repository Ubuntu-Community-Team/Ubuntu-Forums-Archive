---
title: "Weird mouse related issues..."
date: 2010-11-16
forum: General Help
---

### Post by tuthmosis on 2010-11-16
Have multiple symptoms most probably connected to one single bug.

Just installed 10.10 on an old Compaq Presario 2100. (AMD i386)

1) If i reboot without the usb mouse conected, the boot process freezes at the Ubuntu logo. (With dots underline)
2) Sometimes, i have to move the mouse or click the mouse to see the desktop appear after the boot process. Same actions are sometimes necessary to see a closed windows disapear.
3) ScreenSaver's frames freeze unless i move the mouse. Moving the mouse causes the screen to refresh which allows new frames to be painted. This is visible with each and every screensaver.

So... Weird or what ?

---

### Post by yuki-nagato on 2010-11-16
> **tuthmosis said:**
> Have multiple symptoms most probably connected to one single bug.

Just installed 10.10 on an old Compaq Presario 2100. (AMD i386)

1) If i reboot without the usb mouse conected, the boot process freezes at the Ubuntu logo. (With dots underline)
2) Sometimes, i have to move the mouse or click the mouse to see the desktop appear after the boot process. Same actions are sometimes necessary to see a closed windows disapear.
3) ScreenSaver's frames freeze unless i move the mouse. Moving the mouse causes the screen to refresh which allows new frames to be painted. This is visible with each and every screensaver.

So... Weird or what ?

some graphics cards have terrible drivers that will cause that sort of behavior.  Of course, it may also be a bad xorg configuration...

a few questions about the setup:

1) How much RAM is available on the machine?
2) what model graphics card does it use?  (use the lspci command to determine this)
[http://www.ehow.com/how_4742561_which-graphics-card-have-ubuntu.html](http://www.ehow.com/how_4742561_which-graphics-card-have-ubuntu.html)
3) which driver are you using?
[http://ubuntuforums.org/showthread.php?t=228304](http://ubuntuforums.org/showthread.php?t=228304)

---

### Post by tuthmosis on 2010-11-17
Thanks Yuki...

**1) Mem (From /proc/meminfo)**
MemTotal:         442764 kB
MemFree:           14088 kB
Buffers:           33404 kB
Cached:           204380 kB
SwapCached:            0 kB

**2) Video card**
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

**3) Video Drivers**
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Video
    Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]
    Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

---

### Post by yuki-nagato on 2010-11-17
Radeon is one of the two major drivers used with ATI cards; the other being fglrx (which is an evil proprietary 3d accelerated card driver) you may be able to use fglrx instead however, since that install is using pretty much all the memory your computer has, that might be part of it as well as a typical card uses ~128 megs of RAM to display video.  XFCE which is based off of some of the same libraries Gnome is uses significantly less RAM while being quite usable.

---

