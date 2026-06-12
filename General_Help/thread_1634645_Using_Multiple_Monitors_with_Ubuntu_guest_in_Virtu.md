---
title: "Using Multiple Monitors with Ubuntu guest in VirtualBox"
date: 2010-11-30
forum: General Help
---

### Post by willmcmain on 2010-11-30
Here's my setup:
I'm running Ubuntu 10.10 x64 as a guest in VirtualBox on top of Windows 7. I recently bought a second monitor, and I want to set up my Ubuntu guest to use both monitors. 

I configured VirtualBox to give two displays to the VM, and two windows are displayed when I run the VM, however, the Ubuntu guest only uses the primary screen and does nothing with the second--the second screen is just black. When I go to the monitor settings, only the one monitor is detected (as an "unknown monitor")  I have the latest guest additions installed, and the driver under  System-Administration->Additional Drivers is shown as installed and  working correctly. I don't have any issues with the single display--it shows in the correct resolution, and works fine if I set it to fullscreen or seamless mode. Any thoughts on getting Ubuntu to detect the other screen?

---

### Post by uriel1998 on 2010-11-30
Are you sure it's not a VirtualBox problem?  I have XP in a VirtualBox (OSE) install, and it refuses to even admit that there's another monitor.  Have you asked on the VirtualBox forums?

I'm presuming you have a LiveCD about - or at least the ISO for one - does the behavior replicate when running an Ubuntu LiveCD?

And finally, inside the VM, what, if anything, does [FONT=Courier New]xrandr[/FONT] (run from the terminal) report?

---

