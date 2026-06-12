---
title: "Unity 3D not working properly"
date: 2012-04-22
forum: General Help
---

### Post by eabel on 2012-04-22
Ubuntu 11.10 is a VM running on Oracle 4.1.12 with windows & linux guest extentions.  All was working fine until I loaded and configured CPAN's OPENGL ver.066, now Unity3D locks up if ALT+TAB is entered.  Get the following from the Unity 3D utility:
unity_support_test -p                                                     
OpenGL vendor string:   Mesa Project <-- Was Humper
OpenGL renderer string: Software Rasterizer <- Was Chromium
OpenGL version string:  1.4 (2.1 Mesa 7.11)
Not software rendered:    no  <-- All were yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes
Unity 3D supported:       no
 
did I break this with OPENGL Perl support from CPAN? How can I fix it?  I would if possible like to keep the CPAN OpenGL support if possible as I am interested in learning Perl OpenGL programming.
 
Any help would be appreciated,
 
Best Regards,
 
Ed

---

### Post by ravisghosh on 2012-05-10
I am having the same problem with no resolution found yet.

> shantanu@GreenHead:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string:  1.4 (2.1 (3.3.11627 Compatibility Profile Context))

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no


---

### Post by eabel on 2012-05-10
Okay, I got my system back from the dead.  Please remember that I am running Ubuntu 11.10 through Oracle Vbox.  The issue was the CPAN OpenGL modules.  I had to back out freeglut3, freeglut3-dev, binutils-gold and export LIBGL_ALWAYS_INDIRECT=1, after all was removed and reboot, I was back to normal.  I even have compiz cube running now.
 
Ed

---

### Post by ravisghosh on 2012-05-15
eabel - Could you please elaborate what exactly you did. I am on 12.04 and stuck with same issue. The workstation is not dead and I am able to login but only with 2D Unity.

---

### Post by eabel on 2012-05-15
Okay let me explain, first DEAD was a figure of speech meaning in my case OpenGL was broken.  So all worked fine on my Oracle VM running Ubuntu 11.10 until I added the OpenGL PM for GLUT from CPAN, this caused me to add freeglut3 freeglut3-dev and binutils-gold, almost got OpenGL working for Perl development, I lacked on thing: export LIBGL_ALWAYS_INDIRECT=1, once these steps were perfomed all Perl OpenGL scripts ran, but the result was Unity #D broke.    I worked with Oracle TS as the issue seemed to be the vbox video driver, turns out with the vbox video driver I could not emulate some of the native OpenGL hardware commands, thus I was forced into software emulation.  To undo the mess I created, I just removed freeglut3 freeglut3-dev and binutils-gold and the export of LIBGL, rebooted and that solved my issue.  I now have all my OpenGL development running on Win7 since I could not make it work via hardware in Ubuntu running as a guest on Oracle VirtualBOX.
 
I have read the ATI graphics cards have issuses with OpenGL and can causethe same type of software fall backack.  My laptop runs an AMD880 graphics chipset then emulates ATI Radon 4250 Graphics.  You might want to look on the ATI Web site and get their Linux drivers, do this only if you are not running in a VM like I am, in a VM you are stuck with the drivers the VM vendor supplies.
 
Hope this helps.
 
Ed

---

### Post by eabel on 2012-05-15
Snippet of Xorg.0.log 
 
[    20.500] drmOpenByBusid: drmOpenMinor returns 13
[    20.500] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    20.500] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.500] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/vboxvideo_dri.so
[    20.501] (II) Next line is added to allow vboxvideo_drv.so to appear as whitelisted driver
[    20.501] (II) The file referenced, is *NOT* loaded
[    20.501] (II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
[    20.501] (II) AIGLX: vboxvideo does not export required DRI extension
[    20.502] (II) AIGLX: Trying DRI driver /usr/lib/dri/vboxvideo_dri.so
[    20.503] (II) Next line is added to allow vboxvideo_drv.so to appear as whitelisted driver
[    20.503] (II) The file referenced, is *NOT* loaded
[    20.503] (II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
[    20.503] (II) AIGLX: vboxvideo does not export required DRI extension
[    20.503] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri-alternates/vboxvideo_dri.so
[    20.503] (II) AIGLX: dlopen of /usr/lib/x86_64-linux-gnu/dri-alternates/vboxvideo_dri.so failed (/usr/lib/x86_64-linux-gnu/dri-alternates/vboxvideo_dri.so: cannot open shared object file: No such file or directory)
[    20.503] (II) AIGLX: Trying DRI driver /usr/lib/dri-alternates/vboxvideo_dri.so
[    20.503] (II) AIGLX: dlopen of /usr/lib/dri-alternates/vboxvideo_dri.so failed (/usr/lib/dri-alternates/vboxvideo_dri.so: cannot open shared object file: No such file or directory)
[    20.503] (EE) AIGLX: reverting to software rendering  <-- Look here in the file.
[    20.503] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
[    20.508] (II) AIGLX: Loaded and initialized swrast
[    20.508] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    20.509] (II) VBoxVideo(0): Setting screen physical size to 338 x 158
[    20.545] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.554] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.554] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.554] (II) LoadModule: "evdev"
[    20.555] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.556] (II) Module evdev: vendor="X.Org Foundation"
[    20.556]  compiled for 1.10.2, module version = 2.6.0
[    20.556]  Module class: X.Org XInput Driver
[    20.556]  ABI class: X.Org XInput driver, version 12.3
[    20.556] (II) Using input driver 'evdev' for 'Power Button'
[    20.556] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so

If you look above where I marked look here, you see that the DRI extenstions are not supported, this causes the loading of swrast_dri.so for software rendering, this in turn causes unity_support_test -p to report the erros you see.  As I stated if this is a VM, then the steps I took solved my issue the the Vbox video driver and as I stated there are issues with the ATI driver, but this gives you a place to look.  If yousee failback to sw rastering, then I would troubleshoot a driver graphics issue.  Again, I hope this helps.
 
Ed

---

