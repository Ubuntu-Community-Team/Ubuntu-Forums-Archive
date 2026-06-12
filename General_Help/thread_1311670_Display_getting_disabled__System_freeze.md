---
title: "Display getting disabled / System freeze"
date: 2009-11-02
forum: General Help
---

### Post by Tetert on 2009-11-02
Hi there.

I decided to switch to Ubuntu for my home PC.
I have not a lot of experience with Linux, but I'm familiar with the basics.

I'm running a Ubuntu 8.04 with all the updates installed.

I first noticed that my screen was going black while I was playing videos.
I noticed that I was not using the NVidia driver.
After activating it, more trouble started.
The screen is disabling after a while, even when just browsing. Some other times, the system freezes totally.

I then tried to install the last driver from NVidia. After a bit of a struggle, I managed to install it.

But the problem is still present.

I checked the messages file, and I spotted those :

Nov  2 21:19:56 Tetert kernel: [   59.731241] NVRM: API mismatch: the client has the version 190.42, but
Nov  2 21:19:56 Tetert kernel: [   59.731244] NVRM: this kernel module has the version 71.86.04.  Please
Nov  2 21:19:56 Tetert kernel: [   59.731246] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  2 21:19:56 Tetert kernel: [   59.731247] NVRM: components have the same version.
Nov  2 21:20:01 Tetert kernel: [   64.921162] NVRM: API mismatch: the client has the version 190.42, but
Nov  2 21:20:01 Tetert kernel: [   64.921165] NVRM: this kernel module has the version 71.86.04.  Please
Nov  2 21:20:01 Tetert kernel: [   64.921166] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  2 21:20:01 Tetert kernel: [   64.921168] NVRM: components have the same version.
Nov  2 21:20:07 Tetert kernel: [   70.117467] NVRM: API mismatch: the client has the version 190.42, but
Nov  2 21:20:07 Tetert kernel: [   70.117470] NVRM: this kernel module has the version 71.86.04.  Please
Nov  2 21:20:07 Tetert kernel: [   70.117471] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  2 21:20:07 Tetert kernel: [   70.117473] NVRM: components have the same version.

I'm not sure what to do there. Any idea guys ?

---

### Post by Giblet5 on 2009-11-02
Edit your /etc/X11/xorg.conf and search for the word "nvidia" in quotes. Change that to "nv" and save it. Then hit CtrlAltBackspace and log in.

The Nvidia installer has an option to remove the driver. Do that.

Now, click System -> Administration -> Hardware. Activate the 185... nvidia driver.

When that install completes, hit CtrlAltBackspace again (to restart X with the new driver).

You should be good to go and you'll get notifications of driver updates via update-manager.

---

### Post by Tetert on 2009-11-02
Thanks a lot for this.
I just followed the steps, I will let you know how it goes.

Thanks again :)

---

### Post by Tetert on 2009-11-03
Ok, here is the situation now :


[LIST]
[*]The system keeps freezing, but the time between 2 freezes is longer.
[*]The resolution can't be higher than 800x600
[/LIST]
The errors in the /var/log/messages are still there :

Nov  3 13:34:18 Tetert kernel: [   70.120651] NVRM: API mismatch: the client has the version 169.12, but
Nov  3 13:34:18 Tetert kernel: [   70.120653] NVRM: this kernel module has the version 71.86.04.  Please
Nov  3 13:34:18 Tetert kernel: [   70.120655] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  3 13:34:18 Tetert kernel: [   70.120656] NVRM: components have the same version.

---

### Post by Giblet5 on 2009-11-03
It looks like you still have another nvidia driver installed.

Can you please open a terminal and post the output of these command strings:

```
sudo dpkg -l | grep nvidia
```

and

```
locate nvidia
```

---

### Post by Tetert on 2009-11-03
Sure :

sudo dpkg -l | grep nvidia
ii  nvidia-glx-new                             169.12+2.6.24.18-25.2                                NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                                    NVIDIA binary kernel module common files


tetert@Tetert:~$ locate nvidia
/etc/apparmor.d/abstractions/nvidia
/etc/default/nvidia-kernel
/etc/devfs/conf.d/nvidia-kernel-nkc
/etc/init.d/nvidia-kernel
/etc/modprobe.d/nvidia-kernel-nkc
/etc/modutils/nvidia-kernel-nkc
/etc/rc1.d/K20nvidia-kernel
/etc/rc2.d/S20nvidia-kernel
/etc/rc3.d/S20nvidia-kernel
/etc/rc4.d/S20nvidia-kernel
/etc/rc5.d/S20nvidia-kernel
/home/tetert/.nvidia-settings-rc
/home/tetert/.macromedia/Flash_Player/#SharedObjects/YWVY4NNL/www.nvidia.co.uk
/home/tetert/.macromedia/Flash_Player/#SharedObjects/YWVY4NNL/www.nvidia.co.uk/s_br.sol
/home/tetert/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.nvidia.co.uk]("http://www.nvidia.co.uk")
/home/tetert/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.nvidia.co.uk/settings.sol]("http://www.nvidia.co.uk/settings.sol")
/lib/linux-restricted-modules/.nvidia_new_installed
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_legacy
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia/nv-i2c.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia/nv-kernel.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia/nv-vm.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia/nv.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia/nvidia.mod.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia/os-agp.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia/os-interface.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia/os-registry.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_legacy/nv-kernel.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_legacy/nv-vm.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_legacy/nv.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_legacy/nvidia.mod.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_legacy/os-agp.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_legacy/os-interface.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_legacy/os-registry.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/nv-i2c.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/nv-kernel.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/nv-vm.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/nv.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/nvacpi.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/nvidia.mod.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/os-agp.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/os-interface.o
/lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/os-registry.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_legacy
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia/nv-i2c.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia/nv-kernel.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia/nv-vm.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia/nv.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia/nvidia.mod.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia/os-agp.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia/os-interface.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia/os-registry.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_legacy/nv-kernel.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_legacy/nv-vm.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_legacy/nv.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_legacy/nvidia.mod.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_legacy/os-agp.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_legacy/os-interface.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_legacy/os-registry.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/nv-i2c.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/nv-kernel.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/nv-vm.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/nv.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/nvacpi.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/nvidia.mod.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/os-agp.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/os-interface.o
/lib/linux-restricted-modules/2.6.24-25-generic/nvidia_new/os-registry.o
/lib/modules/2.6.24-16-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/video/nvidia
/lib/modules/2.6.24-16-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.24-25-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.24-25-generic/kernel/drivers/video/nvidia
/lib/modules/2.6.24-25-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/usr/bin/nvidia-bug-report.sh
/usr/bin/nvidia-xconfig
/usr/lib/libnvidia-cfg.so.1
/usr/lib/libnvidia-cfg.so.169.12
/usr/lib/libnvidia-tls.so.1
/usr/lib/libnvidia-tls.so.169.12
/usr/lib/nvidia
/usr/lib/directfb-1.0-0/gfxdrivers/libdirectfb_nvidia.so
/usr/lib/nvidia/libGL.so.1.2.xlibmesa
/usr/lib/nvidia/libGL.so.1.xlibmesa
/usr/lib/nvidia/libglx.so.xserver-xorg-core
/usr/lib/nvidia/tls_test
/usr/lib/nvidia/tls_test_dso.so
/usr/lib/tls/libnvidia-tls.so.1
/usr/lib/tls/libnvidia-tls.so.169.12
/usr/lib/xorg/modules/libnvidia-wfb.so.1
/usr/lib/xorg/modules/libnvidia-wfb.so.169.12
/usr/lib/xorg/modules/drivers/nvidia_drv.so
/usr/lib32/nvidia
/usr/share/nvidia-kernel-common
/usr/share/app-install/desktop/nvidia-driver-legacy.desktop
/usr/share/app-install/desktop/nvidia-driver-new.desktop
/usr/share/app-install/desktop/nvidia-driver.desktop
/usr/share/app-install/desktop/nvidia-settings.desktop
/usr/share/bug/nvidia-glx-new
/usr/share/bug/nvidia-glx-new/script
/usr/share/doc/nvidia-glx-new
/usr/share/doc/nvidia-kernel-common
/usr/share/doc/nvidia-glx-new/NVIDIA_Changelog.gz
/usr/share/doc/nvidia-glx-new/README.Debian
/usr/share/doc/nvidia-glx-new/README.txt.gz
/usr/share/doc/nvidia-glx-new/changelog.Debian.gz
/usr/share/doc/nvidia-glx-new/copyright
/usr/share/doc/nvidia-glx-new/examples
/usr/share/doc/nvidia-glx-new/nvidia-settings-user-guide.txt
/usr/share/doc/nvidia-glx-new/examples/XF86Config.sample.gz
/usr/share/doc/nvidia-kernel-common/README.Debian
/usr/share/doc/nvidia-kernel-common/changelog.gz
/usr/share/doc/nvidia-kernel-common/copyright
/usr/share/hal/fdi/information/10freedesktop/21-video-quirk-nvidia.fdi
/usr/share/jockey/handlers/nvidia.py
/usr/share/jockey/handlers/nvidia.pyc
/usr/share/jockey/modaliases/disable-upstream-nvidia
/usr/share/lintian/overrides/nvidia-glx-new
/usr/share/linux-restricted-modules/2.6.24-16-generic/modules.alias.override/nvidia
/usr/share/linux-restricted-modules/2.6.24-25-generic/modules.alias.override/nvidia
/usr/share/man/man1/nvidia-xconfig.1.gz
/usr/share/nvidia-kernel-common/nvidia-kernel.modules.devfs
/usr/share/pixmaps/nvidia-settings.png
/usr/src/linux-headers-2.6.24-16/drivers/video/nvidia
/usr/src/linux-headers-2.6.24-16/drivers/video/nvidia/Makefile
/usr/src/linux-headers-2.6.24-16-generic/include/config/agp/nvidia.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/fb/nvidia
/usr/src/linux-headers-2.6.24-16-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/fb/nvidia/backlight.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/fb/nvidia/i2c.h
/usr/src/linux-headers-2.6.24-25/drivers/video/nvidia
/usr/src/linux-headers-2.6.24-25/drivers/video/nvidia/Makefile
/usr/src/linux-headers-2.6.24-25-generic/include/config/agp/nvidia.h
/usr/src/linux-headers-2.6.24-25-generic/include/config/fb/nvidia
/usr/src/linux-headers-2.6.24-25-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-2.6.24-25-generic/include/config/fb/nvidia/backlight.h
/usr/src/linux-headers-2.6.24-25-generic/include/config/fb/nvidia/i2c.h
/var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.18-25.2_i386.deb
/var/cache/jockey/nvidia.oldconf
/var/lib/dpkg/info/nvidia-glx-new.list
/var/lib/dpkg/info/nvidia-glx-new.md5sums
/var/lib/dpkg/info/nvidia-glx-new.postinst
/var/lib/dpkg/info/nvidia-glx-new.postrm
/var/lib/dpkg/info/nvidia-glx-new.preinst
/var/lib/dpkg/info/nvidia-glx-new.prerm
/var/lib/dpkg/info/nvidia-glx-new.shlibs
/var/lib/dpkg/info/nvidia-kernel-common.conffiles
/var/lib/dpkg/info/nvidia-kernel-common.list
/var/lib/dpkg/info/nvidia-kernel-common.md5sums
/var/lib/dpkg/info/nvidia-kernel-common.postinst
/var/lib/dpkg/info/nvidia-kernel-common.postrm
/var/lib/dpkg/info/nvidia-kernel-common.prerm
/var/log/nvidia-installer.log

---

### Post by Giblet5 on 2009-11-03
Please repeat the trick to disable the nvidia driver (edit /etc/X11/xorg.conf ```
sudo gedit /etc/X11/xorg.conf
``` change "nvidia" to "nv") and restart the X server via Ctrl-Alt-Backspace.

[COLOR="DarkRed"]NOTE: I assume that your system is perfectly stable in this mode.[/COLOR] If that is not the case, please tell me and don't proceed with the following.

Now, remove the nvidia package and the driver modules from the older driver installs:
```
sudo apt-get remove nvidia-glx-new
## You might want to use copy/paste here...
sudo rm -fr /lib/linux-restricted-modules/2.6.24-16-generic/nvidia* /lib/linux-restricted-modules/2.6.24-25-generic/nvidia*
```

And move your nvidia settings to backup: ```
mv ~/.nvidia-settings-rc ~/.nvidia-settings-rc.maybebad
```

Now install the Ubuntu "restricted" nvidia driver again. It will say you need to reboot, but CtrlAltBackspace does the same thing - it restarts Xorg.

Log back in. If the behavior persists, please post the contents of /var/log/Xorg.0.log and ~/.xsession-errors and enclose those in CODE blocks (click the "#" in the toolbar of the forum message editor before pasting).

---

### Post by Tetert on 2009-11-03
As far as I see, the is no "nvidia" in the X config file, only "nv"
The system keeps crashing.

When I check in the "Hardware drivers", I notice the Enabled is unticked, but the status is "In use". Is that normal ?

---

### Post by Giblet5 on 2009-11-03
> **Tetert said:**
> As far as I see, the is no "nvidia" in the X config file, only "nv"
The system keeps crashing.

When I check in the "Hardware drivers", I notice the Enabled is unticked, but the status is "In use". Is that normal ?

I think we have another problem. Possibly hardware. If you haven't done so in the past three months, this would be an excellent time to power down your system, take off the skins, drag it outside and use an air can to blow all of the dust out of the cabinet and from around the cpu and video card fans.

Overheating looks exactly like this.


Assuming it's all clean and cool:

Can you post the output of ```
xdpyinfo
``` within CODE blocks, please?

---

### Post by Tetert on 2009-11-03
Ok, just so you know, I replaced the screen I was using by another one just now.
I can use 1024x768 now.

I also cleaned the dust in there.

```
tetert@Tetert:~$ xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10400090
X.Org version: 1.4.0.90
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x2e00021, revert to Parent
number of extensions:    30
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XAccessControlExtension
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-Misc
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1024x768 pixels (342x271 millimeters)
  resolution:    76x72 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x5d
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa8033
    KeyPressMask             KeyReleaseMask           EnterWindowMask          
    LeaveWindowMask          ExposureMask             StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       ColormapChangeMask       
  number of visuals:    3
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5b
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
```

---

### Post by Giblet5 on 2009-11-03
Is it stable with this CRT?

If so, I suspect the other monitor...

---

### Post by Tetert on 2009-11-03
Regarding the temperature, when I compiled and used the driver from the Nvidia website, I was able to see a temperature of 63 degrees on the GPU, with a warning at 117 degrees.

---

### Post by Tetert on 2009-11-03
There is no change apart from the resolution. Same issue.
Also, it was all fine under Windows XP 2 days ago.

---

### Post by Tetert on 2009-11-03
I noticed something interesting.
If I surf some websites with flash, the system will freeze.
If I play an .avi file, the screen will go black.

If I surf webpages with no flash, if I use OpenOffice or if I leave the system idling, no problem at all.

It's getting weirder and weirder.

Do you think upgrading to the 9.10 might help ?

Edit :
It seems that going back to 800x600 helps to avoid the system to crash.

---

### Post by Giblet5 on 2009-11-03
> **Tetert said:**
> I noticed something interesting.
If I surf some websites with flash, the system will freeze.
If I play an .avi file, the screen will go black.

If I surf webpages with no flash, if I use OpenOffice or if I leave the system idling, no problem at all.

It's getting weirder and weirder.

Do you think upgrading to the 9.10 might help ?


9.10 runs flawlessly on this system. That doesn't mean it will run flawlessly on your system, of course, but there is certainly more focus on fixing 9.10 issues right now.

I only ran 8.04 for a month before installing the Intrepid alpha: even the 8.10 alpha was more stable than 8.04. Again, that's just MY experience.

I would certainly consider upgrading if I were you and having this trouble with my system, but I would try running for a day off of the 9.10 Live CD first. That will give you a feel for the obvious issues (if any).

---

### Post by Tetert on 2009-11-03
True.
As this install is only 2 days old, I can just reinstall with the 9.10.
I will first try to run it off the live CD to see if it is OK.

Thanks a lot for all your help on this.

---

### Post by Giblet5 on 2009-11-03
> **Tetert said:**
> True.
As this install is only 2 days old, I can just reinstall with the 9.10.
I will first try to run it off the live CD to see if it is OK.

Thanks a lot for all your help on this.

You're welcome. Better luck with 9.10! I like it so far, as in best-yet.

---

