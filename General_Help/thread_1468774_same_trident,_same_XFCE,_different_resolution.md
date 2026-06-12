---
title: "same trident, same XFCE, different resolution"
date: 2010-05-01
forum: General Help
---

### Post by caieng on 2010-05-01
My first post: sorry if it is in the wrong section of the forum.  Please feel free to move it to a more appropriate location if desired.

Problem:  I have a few older computers, well, several, half a dozen, and some of them work very well, with OTHER versions of Linux, but not with Ubuntu, Xubuntu, Debian, Mint, or other derivatives therefrom.  More precisely, the video resolution is inadequate (800 x 600) under the latter distributions, though normal {1024 x 768} with Mandriva, PCLinuxOS, Puppy, and others....

In particular, comparing XFCE with Ubuntu, i.e. Xubuntu, and PCLinuxOS XFCE, there is a striking difference.  Xubuntu has the NEWER version of X.org, and clearly, studying the log file, once observes that the OS did recognize the video controller, and did load the appropriate drivers.  So, why doesn't Xubuntu (or any other Debian distro) display correctly, or at least, offer the user a choice?  With PCLinuxOS XFCE the user doesn't have to engage in ANY activity, none, not a thing, to observe a desktop functioning correctly at 1024 x 768.  Ditto for Mandriva with KDE.  Puppy does require the user to choose the proper resolution, instead of choosing it automatically, but, the point is, the resolution is correct.  Why is it NOT correct, and NOT amenable to correction with Ubuntu, and all the other Debian distros?

WHY?

So, first I checked the forum search engine:

[http://ubuntuforums.org/showthread.php?t=1464544&highlight=trident](http://ubuntuforums.org/showthread.php?t=1464544&highlight=trident)

and 
I visited Google:

[http://www.danielbaer.com/danielbaer/drb/drupal/node/6](http://www.danielbaer.com/danielbaer/drb/drupal/node/6)

To no avail.

So, I thought of registering here, to ask for some assistance.

Rather than cutting and pasting the WHOLE of Xorg.0.log for the two versions, I thought it may be sufficient to paste in a couple of short passages, but, if not, then, I will be glad to post the two complete files, if that would assist someone in explaining:

a.  Why Xubuntu cannot display 1024 x 768, but an even less modern version of XFCE from PCLinuxOS can, and does, easily?

b.  more importantly, HOW can I fix this problem?

Here's a couple of tiny excerpts from Xorg.0.log for Xubuntu:

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux t2 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC
2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=d825c144-
7fd8-481e-b24f-49cd46a646f3 ro quiet splash
Build Date: 23 April 2010  05:11:50PM

...

(--) PCI:*(0:1:0:0) 1023:8500:1023:8500 Trident Microsystems CyberBlade/i1 rev 106, Mem @
0xe5800000/8388608, 0xe6000000/131072, 0xe5000000/8388608, BIOS @ 0x????????/65536

...

(II) Loading extension DRI2
(==) Matched trident as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
    compiled for 1.7.2, module version = 1.3.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0

....
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for trident
(--) Assigning device section with no busID to primary device
(--) Chipset cyberbladei1 found
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) TRIDENT(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) TRIDENT(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"

.....

That may not be enough, so, if necessary, I can submit the entire file to the forum.

here is the comparable data from PCLinuxOS XFCE, from 25 April 2010

X.Org X Server 1.6.5
Release Date: 2009-10-11
X Protocol Version 11, Revision 0
Build Operating System: Linux_2.6.32.4-pclos2 PCLinuxOS
Current Operating System: Linux localhost.localdomain 2.6.32.11-pclos2.bfs #1 SMP PREEMPT Wed Apr 7 13:33:19 CDT 2010 i686
Build Date: 22 January 2010  05:01:40AM

....
(--) PCI:*(0:1:0:0) 1023:8500:1023:8500 Trident Microsystems CyberBlade/i1 rev 106, Mem @ 0xe5800000/8388608, 0xe6000000/131072, 0xe5000000/8388608, BIOS @ 0x????????/65536

.....

(II) Loading extension DRI2
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
    compiled for 1.6.5, module version = 1.3.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) v4l driver for Video4Linux

.....

(**) TRIDENT(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.5, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) TRIDENT(0): RGB weight 888
(==) TRIDENT(0): Default visual is TrueColor
(==) TRIDENT(0): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(0): Using XAA for acceleration


Thanks for any suggestions.

CAI ENG
:)

---

### Post by caieng on 2010-05-06
solved it.
short answer:  create new file called xorg.conf  located in /etc/X11
This file must contain monitor and video controller specific information best obtained from consulting the log files located at /var/log.
here's a couple of other forum references:
[http://ubuntuforums.org/showthread.php?t=806835&page=2](http://ubuntuforums.org/showthread.php?t=806835&page=2)
[http://ubuntuforums.org/showthread.php?t=1102194&page=2](http://ubuntuforums.org/showthread.php?t=1102194&page=2)

This solution works for only one computer at a time, i.e. labor intensive, the result of a defective installer.  The Unity installer, for example, does not compel the user to teach the operating system about the hardware.

Question:  if something this simple can not be properly handled by the Debian/Ubuntu/Mint/Mepis/etc. group, why should a user trust any of the rest of the software?

CAI ENG

):P

---

