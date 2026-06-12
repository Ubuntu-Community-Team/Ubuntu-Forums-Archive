---
title: "Problem with System Monitor"
date: 2009-12-26
forum: General Help
---

### Post by inyourhouse on 2009-12-26
I installed Ubuntu yesterday and it was working fine. However, I then opened System Monitor (which originally worked fine) and for some reason it just came up with some big gray block (see attached image). It continues to do this, despite me restarting. The only application I've installed is VLC Media Player, but I guess that can't have anything to do with this.

:confused:

---

### Post by lidex on 2009-12-26
Looks like you have VLC running. Try closing that first. Are you using the ppa version? I had problems with that.

---

### Post by inyourhouse on 2009-12-26
It still happens when I don't have VLC running. And it's whatever version is on the Software Centre. :(

---

### Post by nerdy_kid on 2009-12-26
do you have compiz running?  kill it, and see if it is better.

---

### Post by lidex on 2009-12-26
Try running it from a terminal and post the output text here.

```
gnome-system-monitor
```

---

### Post by inyourhouse on 2009-12-27
> **nerdy_kid said:**
> do you have compiz running?  kill it, and see if it is better.

How do I do that in terminal? *is a noob*

> **lidex said:**
> Try running it from a terminal and post the output text here.

```
gnome-system-monitor
```

It started just as it did in the first post. :(

---

### Post by efflandt on 2009-12-27
That looks like you may have insufficient video RAM for your resolution/colors.

What does **sudo lspci -v** in a terminal show for your video device?  How much RAM does it have and what is your screen resolution.  If is uses shared system RAM, see if there is a BIOS setting for the amount it can use (CMOS setup from your computer screen before anything starts to boot).

There is some sort of workaround that could be put in an Xorg.conf file, but last time I tried to find that post, I could not (maybe something about direct rendering).

---

### Post by inyourhouse on 2009-12-27
> **efflandt said:**
> That looks like you may have insufficient video RAM for your resolution/colors.

What does **sudo lspci -v** in a terminal show for your video device?  How much RAM does it have and what is your screen resolution.  If is uses shared system RAM, see if there is a BIOS setting for the amount it can use (CMOS setup from your computer screen before anything starts to boot).

There is some sort of workaround that could be put in an Xorg.conf file, but last time I tried to find that post, I could not (maybe something about direct rendering).

This is what I got after putting that in terminal:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
    Subsystem: IBM Device 0530
    Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 3000 [size=256]
    Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: [58] AGP version 2.0
    Capabilities: [50] Power Management version 2
    Kernel modules: radeon, radeonfb
```

Screen resolution is 1024 x 768, but the same thing happens at lower resolutions. And I don't think this video card uses shared memory.

---

### Post by lidex on 2009-12-27
> **inyourhouse said:**
> How do I do that in terminal? *is a noob*



It started just as it did in the first post. :(

Yeah, but what messages did you see in the terminal?

Do it again, then immediately after run this command:
```
dmesg | tail
```

---

### Post by inyourhouse on 2009-12-27
> **lidex said:**
> Yeah, but what messages did you see in the terminal?

Do it again, then immediately after run this command:
```
dmesg | tail
```

Okay, it said this:

```
** (gnome-system-monitor:4404): WARNING **: SELinux was found but is not enabled
```And then after doing that dmesg bit, it says this:

```
[   20.743385] [drm] Loading R100 Microcode
[   20.743439] [drm] writeback test succeeded in 2 usecs
[   21.748696] psmouse serio2: ID: 10 00 64
[   26.159223] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   26.367287] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   80.636043] Clocksource tsc unstable (delta = -220006895 ns)
[  114.844131] lib80211_crypt: registered algorithm 'WEP'
[  116.056357] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  126.588049] eth1: no IPv6 routers present
[37077.215337] ipw2100: Fatal interrupt. Scheduling firmware restart.
```:confused:

---

### Post by lidex on 2009-12-27
Do you have gnome-globalmenu installed? If yes, try disabling or removing it.

---

### Post by Strongman332 on 2009-12-27
you can disable compiz inside of the appearance preferences >> visual effects >> none

---

### Post by inyourhouse on 2009-12-28
> **lidex said:**
> Do you have gnome-globalmenu installed? If yes, try disabling or removing it.

I don't have it installed.

> **Strongman332 said:**
> you can disable compiz inside of the appearance preferences >> visual effects >> none

Oh, I disabled that right after I installed Ubuntu.

---

