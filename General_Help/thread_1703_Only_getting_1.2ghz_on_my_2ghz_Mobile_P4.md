---
title: "Only getting 1.2ghz on my 2ghz Mobile P4"
date: 2004-10-22
forum: General Help
---

### Post by kristiann on 2004-10-22
Hi
Just installed Ubuntu, and loving it.
But I've got a problem with my cpu configuration. This is a Dell Inspirion 8200, with a Mobile P4 2ghz, but it's only running at 1,2ghz (with power supply connected and disconnected). Anyone got any tips on what I should use to get it running at full speed (at least when the power supply is connected). What's the best tool for this?

Thanks,
Kristian

---

### Post by goDez on 2004-10-22
Okay.. This is just a laptop thingie you should not be concerned over. Personlly I have an IBM Thinkpad T42, which runs normally at 1.7 GHz Pentium M (matches around a 3000+ Athlon XP). Although, to save energy (whenever, plugged or unplugged) it will run at a lower CPU speed when it's not needed to run at higher speeds to save power. Normally mine runs at 600Mhz, like now:) When I startup, it goes down from 100% to the 35.. 

Could it be your laptop has the same reasons for being at a lower speed?

---

### Post by kristiann on 2004-10-23
Hi
Thanks, my bad! It was the "powernowd" that did this, it sets the cpu freq according to cpu usage and power supply connection.

- Kristian

---

### Post by kristiann on 2004-10-23
This is strange....
I had a very unplessant experience right now. When uncompressing a couple of files, my laptop started acting really weird, with allot of lag. When checking /proc/cpuinfo, it told me my cpu was running at 2.66ghz, this is as mentioned before a P4 2ghz cpu... I've done nothing with the powernowd settings, or tried doing any manual configuration. 

Is this a bug in powernowd, or in it's default settings? Or some other thing?

Anyone got any tips?
Thanks,
Kristian

---

### Post by butters on 2004-10-23
I've never heard of powernowd, so I disabled it and installed cpufreqd instead.  Edit /etc/cpufreqd.conf and change any processor percentages to actual frequencies in kHz, since the 2.6 kernel no longer supports percentages.  Try adding the cpu frequency scaling monitor to your GNOME panel to see it work.  I thought powernow was a trademark of AMD...

I recompiled my kernel to set the userspace governor as default and compile enhanced speedstep monolithically, but you might not need to do this.  Also, I assume this is a P4-M and not a P-M processor, so it will only support original speedstep.

---

