---
title: "Help!  X/GDM crashes then dies while attempting to restart once per second"
date: 2011-05-29
forum: General Help
---

### Post by redss on 2011-05-29
I have a computer that running Ubuntu 10.04.2 LTS.  

Consistently after a couple hours the X desktop and GDM dies.  It works fine on my other computers but this computer is an intel 2.4 GHz, 1.5 GB.

This can't be duplicated by anything specific, but I know it's not out of RAM at this point.  The console keyboard and mouse are inoperational, and the monitor display seems to be going through test patterns, which turns out to be that the monitor is trying to sync to video output which is switching on about once a second.  I can ssh into the box and see that many processes that were running are no longer running, for example gnome-session... and that once per second there is a new X process invoked with a different auth-for-gem parameter, per below:

/usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-Kynptf/database -nolisten tcp 
(one second later...)
/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-GfBhRk/database -nolisten tcp 
(one second later...)
/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-PribK0/database -nolisten tcp 

How can I troubleshoot this?

-----------------------------

Here is some info from various logfiles:

# dmesg | grep agp
[    4.345441] Linux agpgart interface v0.103
[    4.377791] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    4.378057] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[    4.381363] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000

# dmesg | grep -i vga
[    0.000000] Console: colour VGA+ 80x25
[    0.119552] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.119619] vgaarb: loaded
[    4.517038] vga16fb: initializing
[    4.517045] vga16fb: mapped to 0xc00a0000
[    4.517268] fb0: VGA16 VGA frame buffer device

# tail /var/log/messages
May 28 17:22:22 ubuntu pulseaudio[9271]: pid.c: Stale PID file, overwriting.
May 28 17:22:22 ubuntu pulseaudio[9271]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-i7xEal70Ls: Connection refused

# tail /var/log/Xorg.0.log
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203

Fatal server error:
Failed to submit batchbuffer: Input/output error

# tail /usr/adm/kern.log
May 28 17:45:54 ubuntu kernel: [577246.001043] [drm:i915_gem_idle] *ERROR* hardware wedged
May 28 17:45:55 ubuntu kernel: [577247.175163] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May 28 17:45:55 ubuntu kernel: [577247.488009] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung

---

### Post by redss on 2011-05-31
anybody?

---

