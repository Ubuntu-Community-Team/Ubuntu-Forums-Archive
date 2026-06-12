---
title: "Ubuntu boot issues, possible hardware failure?"
date: 2010-08-29
forum: General Help
---

### Post by falken359 on 2010-08-29
Hi all.

I recently bought a new computer (DELL Inspiron 530 Computer Intel Core2 processor Q6600 (2.40Ghz 1066FSB) w/Quad Core, 8MB cache, 2GB DDR2 SDRAM at 800MHz). I used a LiveCD to install Ubuntu 10.04, and everything was going swimmingly until I started adding other packages/programs in.

I walked away for a few minutes and when I came back the screen was blanked out and wouldn't respond to mouse or keyboard input. I rebooted but as soon as I tried to open Chromium the same thing happened. After another reboot attempt, the screen was off center and ran a massive amount of code across the screen then asked me to enter SETUP.

I enter setup, I've tried to boot from the hard drive and the live CD and neither work, it gives me an off center message:
" ailure

s to enter SETUP"

I'm not sure what's in the lines between. F2 still takes me into setup, but its an infinite loop of not booting.

Any help would be really appreciated. I don't know much about the hardware side, so if there's been some epic failure there, I'm at a loss as to how to proceed. Thanks!

---

### Post by mr clark25 on 2010-08-29
this is not a hardware failure, this is just a bad install of ubuntu.


that message you are seeing is probably a BIOS message saying:
> 
boot failure
press f2 to enter setup


sounds like grub broke. you just need to reinstall grub. you can boot from a live cd and follow the directions here:
[http://mrclark.ath.cx/linux/linux/howchroot.html](http://mrclark.ath.cx/linux/linux/howchroot.html)

---

### Post by falken359 on 2010-08-30
Thank you mr clark, I'll try that as soon as I'm at home and report back!

---

### Post by falken359 on 2010-09-01
Even with boot settings changed, the computer won't boot directly from the live cd. It gives me the same error message after trying to boot up.
I discovered that F1 would get it to boot from the live cd, but now it just endlessly hangs on the splash screen. 

Any of the function keys or esc will get me to a terminal screen, but I can't enter any text, and the same keys all return me to the splash screen. So...progress but not success. Any suggestions for a next step? Thanks for the help!

---

