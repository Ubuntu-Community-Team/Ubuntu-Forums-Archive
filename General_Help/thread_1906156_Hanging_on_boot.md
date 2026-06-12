---
title: "Hanging on boot"
date: 2012-01-08
forum: General Help
---

### Post by FiniteParadox on 2012-01-08
I recently installed 11.10 on my HP Pavilion G4 who's specs are the following:

AMD Dual-Core A4-3300M
AMD Radeon HD 6480G
4GB DDR3 SDRAM (1 DIMM)
HD BrightView LED-backlit Display
SRS Premium Sound with Altec Lansing speakers
(If you need more than this I'll be more than happy to get the info)

Initially I had problems booting from live usb to get Ubuntu installed. I had the black screen issue involving Radeon cards that's been going around, but I managed to boot and install using the commands(I think that is the correct word) "xforcevesa radeon.modeset=0 nomodeset noquiet nosplash".

After I installed I rebooted, and as expected, I got the black screen issue again when I selected Ubuntu from GRUB. So, I rebooted again applying the same boot options from above and I got to the desktop. After updating packages I went to look at my drivers since that was supposedly the cause of the original black screen issue. There were two proprietary graphic drivers listed, they appeared to be exactly the same item listed twice in the menu so I simply installed one and rebooted.

Upon rebooting I applied the boot options a third time, except now I freeze in the command prompt style interface that runs behind the splash images (Bash is the term?). The last message displayed is, "Stopping userspace boot splash [ok]". I'm a novice with linux and beyond the hours of searching for a solution all I've really tried is various combinations of boot options. Removing "quiet" and "splash" and adding "nomodeset" also hangs, but the last message displayed is, "Starting GNOME Display Manager [ok]".

I've messed around with GDM and LightDM, I'm not quite sure what they are but I read some posts saying they were part of the issue. I guess some kinds of logs might be useful to you guys, I can get into a terminal with ctrl + alt + F1 so if you just give me some commands I'll get anything you need.

Thanks!

**EDIT:**
Still playing around with boot options, no success. Help would be appreciated.

**EDIT 2:**
This thread looks interesting, will try the instructions given later and post results.
[http://ubuntuforums.org/showthread.php?t=1862478&highlight=bootsplash](http://ubuntuforums.org/showthread.php?t=1862478&highlight=bootsplash)

---

### Post by FiniteParadox on 2012-01-10
Bump.

---

