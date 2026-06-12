---
title: "boot to console"
date: 2011-02-09
forum: General Help
---

### Post by opitzs on 2011-02-09
Hi all,

is there a way to boot to console, without any x stuff starting?
Background:
I had a problem with my NVidia driver. It stalled the complete system, when X started.
I "solved" that problem by reinstalling. But I still wonder, if there is any way, to supress X on boot, as I would consider that as a very important tool to save your system.

Thanks for your help
Sven

---

### Post by cipherboy_loc on 2011-02-09
Start in recovery mode. If you don't get the GRUB screen on boot, press/hold the shift key while 
booting.


Cipherboy

---

### Post by opitzs on 2011-02-09
I tried that, but alas it seemed to start X, too. However as the system didn't react I can't be 100% sure. It mght have been something different, but that boot logo was not helpful either, as I could not see any output from the starting systems...

Thank you four your help Cipherboy
Sven

---

### Post by Cheesehead on 2011-02-09
That means you're not pressing <shift> early enough. Grub does not start X -never has and never will- it just passes control to whichever OS you choose.

---

### Post by opitzs on 2011-02-09
Hi Cheesehead,

thank you for your help.
OK, let me rephrase anything said. I thought, X was playing havoc with my system, because I changed the driver, rebooted and after booting for a while, around the time X usually starts it hangs, no reply nothing.
The Ubuntu logo prevents me from seeing what happened, Ctrl-Alt-Fx does not work.
Reboot into recovery mode.
Once again the Ubuntu Logo prevents me from seeing anything, once again the system boots into hanging.
Once again I wouldn't even know, where to start looking.

I guess my Problem is the ubuntu logo on start. It prevents me from seeing what happens. Usually I don't care, but when an error needs to be found it can be very irritating.

Thank you
Sven

---

### Post by oldos2er on 2011-02-09
To start in text or console mode, edit /etc/default/grub and change the line GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to GRUB_CMDLINE_LINUX_DEFAULT="text" then run **sudo update-grub**

---

### Post by opitzs on 2011-02-09
Thank you oldos2er,

I will try that!

Thank you very much
Sven

---

