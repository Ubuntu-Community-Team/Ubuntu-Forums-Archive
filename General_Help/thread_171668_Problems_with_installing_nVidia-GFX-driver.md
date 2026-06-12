---
title: "Problems with installing nVidia-GFX-driver"
date: 2006-05-07
forum: General Help
---

### Post by eltongo on 2006-05-07
Hi,

I've managed to install the "nvidia"-driver properly for my recent kernels, but not anymore.

The nvidia-installer.log looks like:

... things gone well so far ...

   [4342754.559000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8756  Wed
   Mar 29 14:26:26 PST 2006
-> Installing both new and classic TLS OpenGL libraries.
-> Parsing log file:
-> done.
-> Validating previous installation:
-> Unable to access previously installed file
   '/usr/lib/tls/libnvidia-tls.so.1.0.8756' (No such file or directory).
-> Unable to access previously installed file
   '/lib/modules/2.6.15.7-kookospaehkinae/kernel/drivers/video/nvidia.ko' (No
   such file or directory).
-> Unable to access previously installed symlink
   '/usr/lib/tls/libnvidia-tls.so.1' (No such file or directory).
-> done.
WARNING: Your driver installation has been altered since it was initially
         installed; this may happen, for example, if you have since installed
         the NVIDIA driver through a mechanism other than the nvidia-installer
         (such as rpm or with the NVIDIA tarballs).  The nvidia-installer will
         attempt to uninstall as best it can.  Please see the file
         '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-8756):
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86 (1.0-8756) is complete.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (1.0-8756):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
ERROR: The runtime configuration check failed for the library
       'libnvidia-tls.so.1.0.8756' (expected:
       '/usr/lib/tls/libnvidia-tls.so.1', found:
       '/usr/lib/libnvidia-tls.so.1').  The most likely reason for this is that
       conflicting OpenGL libraries are installed in a location not inspected
       by `nvidia-installer`.  Please be sure you have uninstalled any
       third-party OpenGL and/or third-party graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

Any ideas?

---

### Post by tseliot on 2006-05-07
Why did you post in this section?
> Warty Warthog 4.10  > Warty 4.10 Application Support  > Ubuntu Live CD

Which version of Ubuntu are you using?

---

### Post by eltongo on 2006-05-07
Uh oh, I'm terribly sorry. I _thought_ I was posting to the video & sound -forum, but somehow it got here.

Well, give some slack for the newcomer. :-)

---

### Post by tseliot on 2006-05-07
My question is the same:
Which version of Ubuntu are you using?

Uninstall the driver:

Press CTRL+ALT+F1 (you'll see ONLY the command line) then type:
```
sudo /etc/init.d/gdm stop (or kdm stop, if you use KDM) 
cd path_to_the_nvidia_installer 
sudo sh name_of_the_installer --uninstall
```

Then:
```
sudo nano /etc/X11/xorg.conf
```
and set the driver to "nv" in the Section Device

Restart x:
```
sudo /etc/init.d/gdm start (or kdm start, if you use KDM)
```

And follow either this guide of mine for [Breezy]("http://www.ubuntuforums.org/showthread.php?t=75074") or this one for [Dapper]("http://www.ubuntuforums.org/showthread.php?t=139264")

If you have any questions you can post them in the thread of the guide you will follow.

Regards

---

### Post by eltongo on 2006-05-07
Oh sorry,

I wasn't so straightforward in my first post. Here's some details:

1) I've compiled the "nvidia"-driver many times before for my 2.6.16.x-kernels (which were self-compiled), but I had to switch back to 2.6.15.17 because of VMWare's lack of support for 2.6.16.x-kernels.
2) I'm currently running the "nv"-driver and running X just fine.
3) I'm running **Breezy Badger**

The problem is this:

ERROR: The runtime configuration check failed for the library
'libnvidia-tls.so.1.0.8756' (expected:
'/usr/lib/tls/libnvidia-tls.so.1', found:
'/usr/lib/libnvidia-tls.so.1'). The most likely reason for this is that
conflicting OpenGL libraries are installed in a location not inspected
by `nvidia-installer`. Please be sure you have uninstalled any
third-party OpenGL and/or third-party graphics driver packages.
-> done.

The nvidia-installer won't go any further because of the problem above. I've tried manually removing those files (libnvidia-tls*), but with no success. I even tried removing the nvidia-glx, as mentioned in your threads, but it didn't help in any way. I have managed to compile my previous nvidia-drivers (the kernel modues) for my previous kernels w/ package nvidia-glx being installed on the system, so I don't think it has nothing to do with it.

What should be removed in order to get the driver installed?

Sinceraly yours,
 d

---

### Post by tseliot on 2006-05-07
Did you uninstall the driver from the installer?:

Press CTRL+ALT+F1 (you'll see ONLY the command line) then type:
```
sudo /etc/init.d/gdm stop (or kdm stop, if you use KDM) 
cd path_to_the_nvidia_installer 
sudo sh name_of_the_installer --uninstall
```

---

### Post by eltongo on 2006-05-07
It doesn't matter whether I uninstall the previous nvidia-driver by that command or not, because the installer does it in any case.

The problem is that the installer detects those libnvidia-tls* files and can't remove them and thus can't install the new kernel module.

---

