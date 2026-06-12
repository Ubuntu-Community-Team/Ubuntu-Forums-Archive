---
title: "Nvidia driver update failed"
date: 2012-08-07
forum: General Help
---

### Post by Absol on 2012-08-07
Hi, i need help regarding the installation of nvidia GTX 550 card driver.
My pc updated this morning and since cant get the nvidia driver working, I tried purging the nvidia-current and then installing it as someone in this thread suggests:
[http://ubuntuforums.org/showthread.php?t=2038770&highlight=nvidia+update](http://ubuntuforums.org/showthread.php?t=2038770&highlight=nvidia+update)
But to no avail.
I got the following output from apt:
```
absol@Freiya:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms
The following NEW packages will be installed:
  dkms nvidia-current
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.5 MB of archives.
After this operation, 98.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mx.archive.ubuntu.com/ubuntu/ precise/main dkms all 2.2.0.3-1ubuntu3 [73.1 kB]
Get:2 http://mx.archive.ubuntu.com/ubuntu/ precise-updates/restricted nvidia-current i386 295.40-0ubuntu1.1 [33.4 MB]
Fetched 33.5 MB in 5min 41s (98.2 kB/s)                                                                                                      
Selecting previously unselected package dkms.
(Reading database ... 423728 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_295.40-0ubuntu1.1_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up nvidia-current (295.40-0ubuntu1.1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic-pae
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Success
INFO:Applying quirk Latitude E6530
DEBUG:{'Files': {}, 'Vendor': {}, 'Monitor': {}, 'Screen': {0: ['\tIdentifier "My Screen"\n', '\tOption "RegistryDwords" "EnableBrightnessControl=1"\n']}, 'Module': {}, 'SubSection': {}, 'DRI': {}, 'InputDevice': {}, 'Extensions': {}, 'InputClass': {}, 'ServerLayout': {}, 'Device': {0: ['\tIdentifier "My Card"\n', '\tDriver "nvidia"\n', '\tOption "NoLogo" "True"\n']}, 'VideoAdaptor': {}, 'Comments': {}, 'ServerFlags': {}, 'Modes': {}}
DEBUG:Creating /usr/share/X11/xorg.conf.d/10-nvidia-current-latitude-e6530.conf
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Success
INFO:Applying quirk ThinkPad T420s
DEBUG:{'Files': {}, 'Vendor': {}, 'Monitor': {}, 'Screen': {0: ['\tIdentifier "My Screen"\n', '\tOption "RegistryDwords" "EnableBrightnessControl=1"\n']}, 'Module': {}, 'SubSection': {}, 'DRI': {}, 'InputDevice': {}, 'Extensions': {}, 'InputClass': {}, 'ServerLayout': {}, 'Device': {0: ['\tIdentifier "My Card"\n', '\tDriver "nvidia"\n', '\tOption "NoLogo" "True"\n']}, 'VideoAdaptor': {}, 'Comments': {}, 'ServerFlags': {}, 'Modes': {}}
DEBUG:Creating /usr/share/X11/xorg.conf.d/10-nvidia-current-thinkpad-t420s.conf
Loading new nvidia-current-295.40 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-27-generic-pae
Building for architecture i686
Building initial module for 3.2.0-27-generic-pae
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-27-generic-pae/updates/dkms/

depmod....(bad exit status: 139)

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 295.40
Kernel:  3.2.0-27-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-27-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 139)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 6
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic-pae
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Previously tried installing the driver version from the nvidia page (295) which was released this month and fixes the security issue, but i seem to have forgotten the way of installing the driver, as multiple errors presented... I'll try google that next.

Any more suggestions?:confused:

---

### Post by efflandt on 2012-08-07
I have not had any problems with GTX 550 Ti in 12.04, other than having to use **nomodeset** during install (no parameters needed after install).  nvidia-current 2.95.40 should have been automatically been installed during Ubuntu installation.

But now your problem may be due to running the script from nvidia website which does not automatically update with kernels and may interfere with automatic updates.  So you may have to run that script from nvidia every time you have a kernel update.  Not sure how you would purge that to use regular Ubuntu packages that would update automatically.

I have never used a pae kernel, I use 64-bit whether I need it (8 GB) or not (2 GB tablet PC).

---

### Post by Absol on 2012-08-08
Hi, thanks for answering, I reached the same conclusion but couldn't find a way to remove the manually installed nvidia driver so I ended installing ubuntu again.

After installation, the fresh Ubuntu 12.04 installation did not started the graphics but afterwards I booted in fail safe mode and then just chose "resume normal boot" which somehow started successfully the graphical environment, installed successfully the restricted drivers and everything seems to work fine now.

I did not allowed the updates though, but might try this weekend.

---

