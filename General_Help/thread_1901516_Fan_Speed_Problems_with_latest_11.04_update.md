---
title: "Fan Speed Problems with latest 11.04 update"
date: 2011-12-28
forum: General Help
---

### Post by SanDiegoSeahawk on 2011-12-28
I've noticed that something has changed with my 11.04 installation that has effected the speed control of my CPU fan.

This was working fine before but now the CPU fan speed seems max'd out.

I read this: [http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31)

Which seems to suggest what the problem might be.  Is anyone else seeing this issue with the it87 module failing to load?  The strange thing is that it seems the fan speed monitoring is working.  

As a side note, I have an ASUS motherboard with Cool 'n Quiet enabled.  I recently had to reset the system CMOS/BIOS and can't be 100% certain that this was when the fan speed problem surfaced.  I  had a video issue on a reboot that forced me to clear the CMOS to get the video to display again.

Has anyone else seen their CPU fan speed max out after a recent update (within the last 3-4 weeks) for Ubuntu 11.04?

---

### Post by SanDiegoSeahawk on 2011-12-28
Nevermind.  This was my bad.  In the process of clearing the CMOS and NOT restoring BIOS defaults the ASUS Quiet Fan features were disabled.

---

