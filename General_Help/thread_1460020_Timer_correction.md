---
title: "Timer correction"
date: 2010-04-22
forum: General Help
---

### Post by Alex Farber on 2010-04-22
I have problems with different current time values on dual-boot computer with Ubuntu 9.10 64 bit and Windows. For example, when I set 13.** in Ubuntu, and reboot to Windows, time is 16.**. I opened computer BIOS setup, and found, that Ubuntu actually shows computer clock time + 3 hours. How can I correct this?

---

### Post by DawieS on 2010-04-22
It seems as if something went wrong with your time-zone selection during installation. Click on the clock and edit your location (add the city closest to you).

Check that you have selected the correct time-zone. The clock should show your local standard time, which should be the same as the BIOS clock. The correct international time is picked up from time-servers.

---

### Post by Alex Farber on 2010-04-22
I tested this on another computer, and found that time shown in Ubuntu is BIOS time + 3 hours, according to selected time zone. It looks like time zone is set incorrectly in the Windows. I will check this.

---

### Post by Alex Farber on 2010-04-25
This looks really strange, after testing I got these results:
Computer with WinXP 32 bit, Ununtu 9.10 32 bit - all timers show the same time (XP, Ubuntu, BIOS).
Computer with Win7 64 bit, Ubuntu 9.10 64 bit: Win7 and BIOS show the same time, Ubuntu shows BIOS time + 3 hours. I have no idea why. The same time zone is selected in all OS.
I solved the problem by selecting the time zone GMT - 3.00 in Ubuntu.  Fortunately, there is some city in Greenland in this time zone :)
I have no explanation for this, but it is working now.

---

### Post by gmargo on 2010-04-25
Try editing the **/etc/default/rcS** file.  An entry in that file says "UTC=yes" or "UTC=no". (This is where Ubuntu stores its idea of your BIOS clock being in UTC or local time.)  Toggle the current value and reboot, and see if that helps.

---

### Post by Alex Farber on 2010-04-26
Setting UTC=no did the trick. Now BIOS and Ubuntu show the same time. Thank you.

---

