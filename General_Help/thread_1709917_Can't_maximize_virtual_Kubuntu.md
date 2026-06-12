---
title: "Can't maximize virtual Kubuntu"
date: 2011-03-19
forum: General Help
---

### Post by TimmyK. on 2011-03-19
Hi, I have Kubuntu running as a virtual machine, with Ubuntu 10.10 as the host. When I maximize it, it only takes up a small part of the screen. This is really annoying, especially when looking at large programs that are too wide. Any way to fix this?

---

### Post by gerowen on 2011-03-19
Reboot the virtual machine with the window maximized.

Linux sometimes does not, in real time, detect the changing availability of possible screen resolutions when running inside Virtualbox.  What I mean is, when your computer boots, Ubuntu scans your existing screen and says, "Oh, the native resolution is 1440x900, let's make that the highest possible setting".  Once it's running at that resolution, it won't re-check unless you disconnect and reconnect that monitor.  What I suspect happens is that you boot the machine with the window not maximized, the guest OS detects that resolution as its "monitor's" native resolution.  When that changes in real time by you resizing the window, the guest Linux OS isn't checking to realize that its resolution can now go up to 1920x1080.  This is supposed to be fixed by installing the Guest Additions that come packaged within Virtualbox.

---

### Post by TimmyK. on 2011-03-19
Nope, didn't do anything.

---

### Post by gmargo on 2011-03-19
Have you installed the VirtualBox guest additions in the Kubuntu virtual machine?

To do that, install these three packages on the guest machine:
virtualbox-ose-guest-dkms
virtualbox-ose-guest-utils
virtualbox-ose-guest-x11

---

