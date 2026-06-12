---
title: "Nvidia GeForce 6100 preventing usable install of Karmic"
date: 2009-11-15
forum: General Help
---

### Post by jimbob on 2009-11-15
Karmic installs fine but comes up with only 800x600 screen resolution.  I notice restriced drivers are available and nvidia-glx-185 is the recommended one so I install it.  When the system is rebooted as suggested the splash screen comes up fine but then my monitor fails over to a tiny box that says "scan rate not supported" and that is the end.
  I ran dkpg-reconfigure -phigh Xserver-Xorg from the command line but it didn't help.
  How can I go in and manually set the resolution and scan rates?
  Any help or insight is appreciated.

---

### Post by jimbob on 2009-11-17
None of the Ubuntu supplied restricted drivers worked on my system.  I ended up going to the Nvidia website and downloading the latest driver 190.42 dated 10/27/2009.
  I then followed these instructions found on linuxforums.org , installed the driver and everything works great.

Installing the Drivers

 

1. Make sure you have the kernel-sources, gcc and make packages installed.

2. Download the latest driver from Nvidia's site.

3. Go into runlevel 3 (no GUI). This can be acheived several ways:

a) By typing CTRL+ALT+F1(or F2-F6), then logging in as root and typing init 3

b) By typing a 3 at the GRUB boot prompt.

c) By editing your /etc/inittab. See below for details.

d) Debian users may need to use /etc/init.d/gdm stop instead.

4. Log in as root user, if you aren't already.

5. Find the driver you just downloaded and run it using something like sh NVIDIA-1.0.8174.run

6. If it gives you an error for rivafb support, ignore it.

7. Stay logged in as root and type modprobe nvidia

NOTE:As of version 8174 of the Nvidia driver, you no longer need to manually edit your xorg.conf file. Skip steps 8 and 9 if you are installing this version or newer.

8. Edit your /etc/X11/xorg.conf in the section marked "Devices" that looks something like this:

 

Section "Device"
    Identifier  "Nvidia Geforce 2"
    Driver      "nv"

 

9. Change the "nv" line to "nvidia"

NOTE: Some distributions use XFree86 instead of X.org. The steps are the same, you're simply editing a different file: the /etc/X11/XF86Config-4 file.

10. Log out as root, and back in as a regular user, then type startx

11. If you see the Nvidia logo flash then you're done. If not your X Windows will error out. Start a thread, post the errors, and we'll try and help you from there.

---

