---
title: "Hard Lockup after installing Netatalk"
date: 2010-02-06
forum: General Help
---

### Post by tji on 2010-02-06
My MythTV backend (Mythbuntu 9.10) has been operating fine, as an HDTV recorder, file server, etc.   I then installed Netatalk (Appletalk file server) in an attempt to improve file sharing with my Mac systems.

Shortly after installing netatalk I started experiencing hard system lockups (non-responsive system,  no ping or even ARP responses, no caps-lock response on keyboard).    I also tried to get info via the magic sysrq key combinations, but got nothing from that (I'm not sure if that works with a USB keyboard or not).

So, I removed the netatalk package and rebooted to remove the appletalk kernel module and clean things out.  Since doing that, I have had no more system lockups.


Hardware:  VIA Artigo A2000 barebones NAS box.  VIA C7 CPU (32 bit x86), 1GB SO-DIMM, 2TB Data Drive, 500GB OS Drive
Software: Clean mythbuntu 9.10 install, operating as a primary MythTV Backend + Samba server.


With netatalk, I got lockups about every 2 days, since removing it, the system has been stable for almost 2 weeks.   I just wanted to post here in case others experience similar issues.  Debugging a hard locked system is pretty difficult.

---

### Post by tji on 2010-02-13
I spoke too fast..

After running the system for another week, and got another hard lockup after removing netatalk.


So, it's obviously not netatalk which is causing the hard lockup.

The chipset + GPU is relatively new (VX800), I guess I'll look into that next.   I also noticed it has a bunch of audio driver kernel modules loaded, which I don't use.   So, I'll see if I can simplify some of those things to gain stability.

---

### Post by tji on 2010-04-19
I turned off X11 / gdm, and removed all the kernel modules I could (via, X, drm, agpgart, all sound modules, parport, iptables, etc).    But, the lockups continue.


I think that with all the GUI modules removed, the GPU is a non-factor (that was what I thought was the most likely candidate for lockups).   It does have the via_velocity ethernet driver, but I think that's used in a lot of systems, so it's less likely to be the issue.

I guess my ext step will be to compile a new kernel, to see if the system gets more stable.  I don't think it's an issue with the hardware.   I ran FreeNAS (freebsd) on it for several months before installing mythbuntu, and it was completely stable.

---

