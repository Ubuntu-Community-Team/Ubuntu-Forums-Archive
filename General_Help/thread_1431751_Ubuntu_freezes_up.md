---
title: "Ubuntu freezes up"
date: 2010-03-17
forum: General Help
---

### Post by lukashjanssen on 2010-03-17
Hi, I've been running Ubuntu for just a little and not long after moving to 9.10 Karmic (not sure if it's related, probably), the system started to have problems in Ubuntu and would freeze up. If anyone could help, I'd be really glad. I dual-boot with XP, and the Windows partition runs just fine. 
what happens is I start up Ubuntu (which seems like its taking longer than usual), and I can run everything perfectly for a few minutes. however, what happens is if I try to use the scroll bar in metacity, firefox, anything, the GNOME desktop environment won't display anything new and I have to minimize/maximize to see anything new on the page. (actually, at the very bottom of the window, the picture WILL scroll, but it's just a tiny line). then, a few minutes usually after booting up, Ubuntu will completely freeze up.
I can move the cursor around as much as I want, but no keystrokes will work, and I can't do anything with the mouse on the screen, apart from move the cursor around.

can anyone help? I've tried doing a little research on the symptoms, but I'm pretty much still a noob, and I need some outside help to diagnose this. It would be greatly appreciated. thanks so much.

---

### Post by ndefontenay on 2010-03-17
Hi.

Can you have a look at your logs? If you can't view them in the menu administration> Log viewer because it's frozen, can you log into a terminal session (ctrl+alt+f1) and then go to /var/log. Look for all related X11 Xorg logs.

You might fins something interesting in it.

to get to /var/log type cd /var/log

To view a file type cat filename (if you are in the folder)

---

### Post by lukashjanssen on 2010-03-17
ok, first thing i happened when I opened log viewer is it said it could not open these (I'm gonna give all the info I can, hopefully some will help):

/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory
/var/log/user.log.0: Error stating file '/var/log/user.log.0': No such file or directory
/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory

then I looked at Xorg.0.log, Xorg.20.log, and 21 and 22. 21, 22, and 23 were identical as far as I could see. I looked at the WW (warning) tags and found these: 

(WW) Falling back to old probe method for sis
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:0:0) found
(--) Assigning device section with no busID to primary device
(--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found

then a bunch of resource ranges before and after probing.

(WW) SIS(0): Could not find/read video BIOS
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor

(the Could not find/read video BIOS also appeare3d in the Xorg.0.log)

then nothing that I thought seemed bad for a while and at the very bottom: 

(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) ImPS/2 Generic Wheel Mouse: Close
(II) UnloadModule: "evdev"
(II) SIS(0): Restoring by setting old mode 0x03
(WW) SIS(0): xf86UnMapVidMem: cannot find region for [0xb769e000,0x10000]
(WW) SIS(0): xf86UnMapVidMem: cannot find region for [0xaf69e000,0x8000000]
 ddxSigGiveUp: Closing log

I really don't know what any of this means, so I'm hoping the community could help me out. thanks.

---

### Post by ndefontenay on 2010-03-17
It looks like you have some problem with your video card which is an SIS chipset. I think I've read somewhere that SIS is not well supported.

Question: did this problem happened recently? 
Do you have it ever since you've installed linux? 
If recently, anything you did that started triggering these?

Are there any dates in those logs? That should help us by telling when the graphic card problems are related to the current freeze.

(the Could not find/read video BIOS also appeare3d in the Xorg.0.log)

If that is the case it might well be a graphic card related problem.

---

### Post by lukashjanssen on 2010-03-17
not too recently, but I've been busy so I just stopped using Ubuntu for a while until I had time to try to fix it. I had Jaunty for quite a long time and then not long after I upgraded to Karmic the problem started (on the same machine). I don't think there was a problem immediately following the installation, but I'm not exactly certain. I feel like it was a little later than that.

to me a graphics card problem makes a lot of sense, from what I've seen. It's strange that this is a new problem for Ubuntu, however. Maybe Jaunty dealt with SIS better?

this Xorg.0.log is from earlier tonight... or at least it had this at the top: 
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 16 10:02:49 2010



(II) Loader running on linux
(++) using VT number 7
(--) PCI:*(0:1:0:0) 1039:6330:103c:2a06 Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter rev 0, Mem @ 0xe0000000/134217728, 0xed000000/131072, I/O @ 0x00009000/128
**(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)**
(II) No APM support in BIOS or kernel

and later in the log:

(==) Matched sis for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.10.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01@00:00:0
**(WW) Falling back to old probe method for sis**
(--) Assigning device section with no busID to primary device
(--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [24] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [25] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [26] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [33] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [34] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.6.0.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0x9000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) SIS(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) SIS(0): Depth 24, (--) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
**(WW) SIS(0): Could not find/read video BIOS**
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is enabled
(II) SIS(0): Using VRAM command queue, size 512k
(==) SIS(0): Hotkey display switching is enabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
        [http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)
(==) SIS(0): DRI disabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".

those are the parts that seemed important.

---

### Post by lukashjanssen on 2010-03-17
I just clicked one of those links at the bottom of the log and what the hell?
Why is a link like that in my log viewer?

---

### Post by Rasa1111 on 2010-03-17
have you disabled the visual effects in system>appearance>visual effects>  none. ? 
might be worth a try if you havent already done so. 

Dont know much about the graphics card work yet. sorry. lol 
 good luck. :)

---

### Post by lukashjanssen on 2010-03-17
yeah, the effects are disabled. thanks though.

I just realized that the other Xorg log files are from October and November (when this problem started, I think). Regardless, they don't show any other problems different than the most recent Xorg logs.

---

### Post by ndefontenay on 2010-03-17
Just looked at the link myself and I'm speechless. Maybe a while before there was some kind of support on this link for sis problems?

Otherwise, now that I get the background of the problem, you should try re-installing again if you don't have too much data. If your problem is still not fixed, it would then be a good idea to file a bug request on launchpad.net.

---

