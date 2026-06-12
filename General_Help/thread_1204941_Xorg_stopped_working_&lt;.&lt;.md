---
title: "Xorg stopped working &lt;.&lt;"
date: 2009-07-05
forum: General Help
---

### Post by del_diablo on 2009-07-05
After a little messing in the xorg.conf for hibirnation/suspend, xorg stopped working.
The exact error is that when its suppose to start doing its wonders, the grapic completely freezez. It still respond to the power button, and the grapic works otherwise(terminalwise and loading screen).

I removed the line, did not solve it. Auto X fix? Did not solve it. Further random frustation attempts? Did not work either <.<
The last time this happend i purged the grapic drivers, but that time i did not install it via the package manager. This time i did, and uninstalling did not do the trick. Purge did not neither. So its either a bug in synaptic that it does not clean the driver, or B: Other random error.

System:
Ati radeon 3460
Radeon 2400 as slave to that
Turion X2 R70
A blackboxed motherboard from fujitsu, and latest BIOS(or so its claimed)
Modified Ubuntu 9.04: Openbox and completely removed GNOME

---

### Post by del_diablo on 2009-07-05
```
delly@delly-laptop:~$ sudo startx --verbose=yes
[sudo] password for delly:

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux delly-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul  5 19:59:11 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7e40
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e60
  XRANDR name: HDMI-0
  Connector: HDMI-B
  DFP1: INTERNAL_UNIPHY
  DDC reg: 0x7e20
finished output detect: 0
Dac detection success
finished output detect: 1
invalid output device for dac detection
finished output detect: 2
finished all detect
before xf86InitialConfiguration
Dac detection success
invalid output device for dac detection
after xf86InitialConfiguration
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
mc fb loc is 00df00c0
(EE) RADEON(0): Acceleration initialization failed
Output DIG dpms success
Output CRT1 disable success
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1280x800 - 1408 816 10
freq: 68900000
best_freq: 68900000
best_feedback_div: 689
best_ref_div: 18
best_post_div: 15
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DIG2 encoder setup success
Output DIG0 transmitter setup success
Output DIG dpms success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output CRT1 disable success
Output DIG dpms success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
/usr/bin/X11/X: symbol lookup error: /usr/lib/xorg/modules/extensions//libdri.so: undefined symbol: atiddxAbiDixLookupPrivate
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
delly@delly-laptop:~$

```

So help..... this disables input on the computer, got the output via ssh.

---

### Post by del_diablo on 2009-07-06
Figured it out, the 1 line change in xorg killed the config. Then auto fix in restore mode did the rest of the misery, which i am gonna report.
The other problem is that by installing the drivers via synapitc a problem is found: it does not give a "want to config your drivers?" dialog, which is a big problem.

---

