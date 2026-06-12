---
title: "Laptop running very hot after upgrade"
date: 2011-11-27
forum: General Help
---

### Post by Falc7 on 2011-11-27
I have just installed Kubuntu 11.10. And the heat that my laptop operates up seems to be 10 degrees centigrade higher when i am just browsing the web. Before it used to be about 51 or so degrees, now i am constantly at 63.

I have implemented this fix
[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

And installed Jupiter and put it on power saving mode, but the temperature still don't go beneath 60 degrees.

I will try a comparison between windows and kubuntu as well.


Edit:
Windows seems to be around the 53-60 range, while not performing any tasks. Within windows, a program called SpeedFan says by GPU fan is 0 RPM, rekon i should contact the manufacturer?

---

### Post by LinuxFan999 on 2011-11-27
Kubuntu is very resource intensive. What are the specifications of your computer?

---

### Post by Falc7 on 2011-11-27
i3
Ati 5650

I play Left 4 Dead 2 with no problems

---

### Post by tersogar on 2011-11-27
Are you using proprietary drivers?

---

### Post by Falc7 on 2011-11-27
There is an ATI graphics card driver listed as being available, but i'm not using it atm

---

### Post by tersogar on 2011-11-27
Open source drivers do not handle the temperature as good a the proprietary ones.

---

### Post by oldtimer7777 on 2011-11-27
> **tersogar said:**
> Open source drivers do not handle the temperature as good a the proprietary ones.

I recommend going into BIOS and setting your CPU fans to operate at the highest settings possible.

---

### Post by Falc7 on 2011-11-27
I've installed the propriatory drivers and it seems to have brought it down to around 57 degrees, which is better.

There are two graphics drivers, the proprietary one, and the post release updates propriety one. The latter sounds like the best one to install, but i get this error message in the log file 

Anyway on the non-post-fix driver, it still seems to be working a bit better.

Unfortunately my bios dosen't seem to have the option to change fans speeds.

Should i be concerned that Speedfan program in windows lists my GPU fan speed as 0?
I think what I will do is get someone at the university to open the laptop up and give the heatsink a good clean, remove the dust that type of thing as well, that should help.

> Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx-updates.
(Reading database ... 125731 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.902-0ubuntu0.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.902-0ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.902-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.902 DKMS files...
Building only for 3.0.0-13-generic
Building for architecture x86_64
Building initial module for 3.0.0-13-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-13-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Setting up fglrx-amdcccle-updates (2:8.902-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-11-27 20:50:24,379 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-11-27 20:50:24,541 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-11-27 20:50:24,682 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-27 20:50:24,682 DEBUG: fglrx_updates is not the alternative in use
2011-11-27 20:50:24,737 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-27 20:50:24,738 DEBUG: fglrx_updates is not the alternative in use


---

### Post by linuxrev on 2011-11-28
Perhaps you could *carefully* open your laptop and see if there is dust cluttering around the fan? If so, remove with a soft brush, or, again *carefully*, with compressed air.

---

