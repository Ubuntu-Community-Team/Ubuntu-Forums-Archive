---
title: "Ubuntu keeps crashing"
date: 2011-11-10
forum: General Help
---

### Post by Daniel15 on 2011-11-10
First time I tried to install Ubuntu, it crashed at the end of the installer. I tried installing it again, and the installation worked, but it crashed as soon as I opened a terminal.

System specs:
 - Asus P8H61-MLX motherboard
 - Intel i5 2400 processor
 - ATI Radeon HD 6670
 - Fresh Ubuntu install

Here's a picture of the crash message: [http://twitpic.com/7coz0z/full](http://twitpic.com/7coz0z/full)

Any ideas?

I'm doing a memory test with Memtest86+ at the moment. it's up to 49% with 0 errors so far.

---

### Post by carranty on 2011-11-10
I'm not sure I can be of much help, but sometimes I've had similar problems when trying to install a new version of linux.  Are you using a live cd?  You could try burning a CD again, on the slowest write speed - sometimes there are errors on the CD that can cause errors during installation and shortly after.  Using the slowest write speed usually prevents these.  Or maybe try installing from USB.

You're not upgrading from an older version are you?  In my experience upgrades can be far more problematic than fresh installs.

If that doesn't work try an older version (10.04 is very stable), you might have more luck and its fully supported for over a year yet.

Hopefully someone with more experience in installation issues can help out, but I'd at least try a different cd, burnt on the slowest speed.

Also, you might have more luck moving this thread to the 'installation and upgrades' forum.

---

### Post by Daniel15 on 2011-11-18
Seems this was due to the ATI "radeon" drivers. Someone in the IRC channel suggested adding "radeon.modeset=1" to my boot options, and this seemed to help. I switched to "fglrx" and the crashes stopped happening. Been using this computer for about a week now with no major issues :)

I also realised I installed a 32-bit version of Ubuntu so I formatted my computer and installed 64-bit instead.

---

