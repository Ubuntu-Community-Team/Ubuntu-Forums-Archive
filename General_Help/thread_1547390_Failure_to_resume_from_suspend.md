---
title: "Failure to resume from suspend"
date: 2010-08-06
forum: General Help
---

### Post by alanwalterthomas on 2010-08-06
My desktop computer intermittently fails to resume from suspend. It's a Gigabyte AMD 780g chipset, ATI Radeon 4670, running 10.04 with Catalyst/FGLRX installed from default ubuntu repository.
After pressing the power button, the computer seems to come to life, but the monitor does not turn on. It's power light keeps flashing in standby mode.
Sometimes suspend works, other times it doesn't, & I'd like to know why & then what I might do about it.
Please let me know what info I should provide & how to provide it if you have any idea of what the cause may be.

I ran the first few iterations of the ubuntu suspend resume stress test ([https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)). The computer suspended, did not resume automatically, but resumed successfully when I manually turned it on, except for the first test when it failed to suspend. I got this output:
*** TEST 1 -- suspend triggered via dbus message
*** machine will suspend for 20 seconds
*** press return when ready


SUSPEND FAILED, did not go to sleep
*** no BATTERY detected ac tests skipped ...
*** no BATTERY detected power test skipped ...

*** TEST 2 -- 30 iteration variable delay suspend/resume stress test
*** machine will suspend for 20 seconds
*** NOTE: there will be no further user interaction from this point
*** press return when ready


delay 60 ...
wait for 60 seconds
delay 58 ...
wait for 58 seconds
delay 56 ...
wait for 56 seconds
delay 54 ...
wait for 54 seconds


Edit:
Of note, when it fails to resume, the computer will have taken about 30 seconds to turn off, against just a few seconds when it will resume.
ssh doesn't work. (no route to host)
Open programs, ~30 firefox tabs, a few gedit text files, transmission, had had to kill frostwire... I think that's it.

---

### Post by alanwalterthomas on 2010-08-08
Bump, it's still happening. This time nothing was opened but firefox. If someone can tell me where to look for error messages I'll post them.

Also, would it possibly do any good to reinstall the FGLRX driver? I've also noticed that after I reboot the computer, networking is disabled, but I can re-enable it without any problems.

Thanks,

---

### Post by alanwalterthomas on 2010-08-17
bump

---

### Post by alanwalterthomas on 2010-08-24
Are there multiple methods that ubuntu uses to suspend?
I have no problems if it suspends after leaving it idle for a while. (suspend after x time in power management settings)
It still doesn't resume if I go to the top right corner & select suspend.

---

### Post by alanwalterthomas on 2010-12-09
Installed 10.10 & used the restricted drivers manager. So far no problems.

---

