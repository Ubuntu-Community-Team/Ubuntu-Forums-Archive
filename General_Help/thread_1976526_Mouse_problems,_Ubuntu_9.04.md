---
title: "Mouse problems, Ubuntu 9.04"
date: 2012-05-08
forum: General Help
---

### Post by Ken_g6 on 2012-05-08
First, I'm still on Ubuntu 9.04; I know I need to upgrade someday, but I never have time to try.

Now, my current symptoms.  When I have a USB mouse plugged in today, it's not recognized in Ubuntu.  It was working for years, until today.  I managed to get my mouse working by plugging it into a laptop next to my desktop and using VNC, but this setup is far from perfect.  The other major symptom is that, every so often, my mouse cursor is overwritten from top to bottom with a square of thin, vertical, purple lines.  If I move the mouse around enough (through VNC), so that the cursor changes, the lines go away for awhile, or at least only cover part of the cursor.

Warnings and errors from /var/log/Xorg.0.log, and output of lspci and lsusb follow:
```
/var/log$ grep '^([WE][WE])' Xorg.0.log
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x61110 (PORT_HOTPLUG_EN) changed from 0x00000120 to 0x00000020
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available
(WW) intel(0): DRI2 requires UXA
(EE) [drm] drmOpen failed.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
(WW) intel(0): PGTBL_CTL (0x00000000) indicates GTT is disabled
(WW) intel(0): Existing errors found in hardware state.
(WW) intel(0): ESR is 0x00000001
(WW) intel(0): PGTBL_CTL (0x00000000) indicates GTT is disabled
(WW) intel(0): Existing errors found in hardware state.
(WW) intel(0): ESR is 0x00000001
(WW) intel(0): PGTBL_CTL (0x00000000) indicates GTT is disabled
(WW) intel(0): Existing errors found in hardware state.
(WW) intel(0): ESR is 0x00000001
(WW) intel(0): PGTBL_CTL (0x00000000) indicates GTT is disabled
(WW) intel(0): Existing errors found in hardware state.

/var/log$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

/var/log$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

As to the cause, my best guess is something stupid I did yesterday.  I'd downloaded the latest tor-browser-gnu-linux-x86_64-2.2.35-11-dev-en-US.tar.gz.  It worked so well I decided to try replacing my main tor binary with the one from that package.  That didn't work, so I copied all the libraries from the Lib directory to /usr/lib.  I thought I wasn't overwriting anything, but it turned out I overwrote four libQt libraries.  I've since deleted all the extra libraries, restored the four libQt binaries from an old drive mirror, and even deleted and replaced my home directory with a backup from Sunday night, rebooting after each time.  One time I got the mouse to move, but I haven't been able to reproduce that, and the purple lines were still there.

Help?

---

### Post by Ken_g6 on 2012-05-09
Morning bump.  Also, another symptom I remembered: The very first thing I noticed was that all my CPU temperature sensors in GKrellm disappeared.  They haven't come back.  This is something else I'd like to fix, but it's minor compared to the mouse issue.

---

### Post by smurphy on 2012-05-09
I bet you have replaced some libraries with broken ones when you installed the browser.

What exactly did you do to install it ?

IMHO - making an upgrade of the system would fix it - as it would replace the files you overwrote with the tar.gz file.
However, this means that the package manager dependencies did not get destroyed too ...

and - do you have a ubuntu 9.04 32Bit or 64Bit system ? The tor-browser you installed is 64bit from the package name.

---

### Post by mörgæs on 2012-05-09
> **Ken_g6 said:**
> First, I'm still on Ubuntu 9.04; I know I need to upgrade someday, but I never have time to try.

You are not saving time by trying to troubleshoot 9.04. The fast solution begins with a fresh install of one of the supported Buntus.

---

