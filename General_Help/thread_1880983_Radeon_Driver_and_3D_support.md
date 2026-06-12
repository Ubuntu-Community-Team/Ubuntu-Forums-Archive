---
title: "Radeon Driver and 3D support"
date: 2011-11-14
forum: General Help
---

### Post by alexneto on 2011-11-14
I'm running Ubuntu 11.10 64 bits with a Radeon HD 5770. I have been using the 3rd party fglrx drivers, but when I tried to change to Gnome-shell I realized that they did not work well together and I tried to go back to RadeonDriver.

I followed the instructions in the FglrxInterferesWithRadeonDriver, in the wiki.

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch ]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch")

I still was not able to use Gnome, and I realized that I had no 3D support. So I decided to install the new fglrx drivers again. After that, Gnome only works in classic mode, and I still with no 3d support.

When I do ```
Sudo fglrxinfo
``` I got the following error message:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

Once again I tried to go back to RadeonDriver. After the reboot, the ubuntu logo appears but then the computer gets inactive and the monitor goes to sleep.

Rebooting in recovery mode, and doing:

```
dmesg | grep drm
```

I got the message:

Initialized drm 1.1.0 20060810
Vgacon disable radeon kernel modesetting
Supports vblank timestamp caching Rev 1 (10.10.2010)
No driver support for vblank timestamp query
Initialized radeon 1.33.0 20080528 for 0000:01:00.0 on minor 0

Any idea of what can I do to solve this problem, and be able to use a driver (don't care wish) that gives me 3d suport and the use of Gnome-shell?

thank you in advance.

Alex

---

