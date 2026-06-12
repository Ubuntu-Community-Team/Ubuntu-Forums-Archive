---
title: "10,04 LTS: xmas updates killed the system"
date: 2010-12-25
forum: General Help
---

### Post by VictorR on 2010-12-25
While installing last updates, which included linux kernel, update manager stopped at
Configuring grub.cfg...
I left the system for about half a day, but it did not get any further.
After reboot it not longer works. On normal boot it displays a message about low resolution mode, but the system's already dead, it only reacts on Reset button.

On recovery mode, regardless of what kernel I selected (2.6.32-26 generic ... 2.6.32-24 generic) it always stops on:
```

Begin: Running /scripts/local-bottom...
Done.
Done.
Begin: Running /scripts/init-bottom...
Done.

```
I looked for similar situations here in he forum, but all suggestions assumed that I can login somehow, but I can't.

The system is
Linux Desktop 2.6.32-26-generic, CPU AMD Athlon XP, NVidia NV17 graphic card with proprietary driver

Any ideas, please.
Any ideas

---

### Post by Monotoko on 2010-12-25
Use a LiveCD to login and then use the "update-grub" command ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)). This should fix the grub manager on your PC.

Merry Christmas!
Daniel

---

### Post by Eventvwr on 2010-12-25
My system is also dead. The updates I ran today (there were a lot, I don't use this PC much) stalled somewhere after the pulseaudio stuff. I had a screen half filled with flashing vertical lines and had no option other than hard power off.

Now when I reboot it comes back to a normal looking desktop but is totally unresponsive

If I reboot in recovery mode (hold shift key and select either of the linux kernels labelled as "recovery mode") the boot process scrolls up the screen until it gets to

Begin: Running /scripts/init-bottom ...
Done.

After this, nothing works. Apart from Ctrl-Alt-Del which reboots it

I am a noob, but this doesn't seem to be a GRUB problem, because I can boot fine and select different boot options. The problem seems to me to be that none of the options lead to a working PC

:(
E

---

