---
title: "Boot Process having a serious hangup"
date: 2009-10-31
forum: General Help
---

### Post by simpleeddie on 2009-10-31
I have a problem with my startup sequence in ubuntu 9.10. I have a fresh install that is taking well over 70 seconds to boot. 

I have set the startup options and removed splash and quiet to have a closer look at the problem.

After the usb devices have been set (usb 1-4, etc etc), the process hangs. Exaclty 20 seconds later, the screen then adds:

[22.012509] ata6: lost interrupt (Status 0x0)
[22.012566] ata6.01 exceptio Emask 0x0 SAct etc etc
[22.012624] ata6.01: cmd a0/01:00:00:00 etc ect
[22.012625]              cdb 12 00 00 00 60 00 00 00 00 00
[22.012626]              res 40/00:02:00:24:00/00:00:00:00

[22.012786] ata6.01: status: { DRDY }
[22.012844] ata6: soft resetting link
[22.250173] ata6.00: configured for UDMA/33
[22.290272] ata6.01: configured for MWDMA2
[22.305112] ata6: EH complete

then another 20 second wait...

[43.010009] ata6: lost interrupt (Status 0x0)
[43.010065] ata6.01: limiting speed to MWDMA1:P104
[43.010115] ata6.01: exception Emask 0x0 SAct 0x0 SErr

it then continues down to "EH complete" and waits a further 20 seconds.

At around 63.01522 it kicks back into the boot process and after another 5-10 seconds, the login screen is ready.

Please help me solve this problem!! I have tried all types of usb combos, the usb does not affect the situation, and I have even taken out an old hard drive in an effort to get the boot time back down to a reasonable speed.

Thanks in advance,
simpleeddie

---

### Post by simpleeddie on 2009-10-31
bump

---

### Post by simpleeddie on 2009-11-01
bump again. Any chance ANYBODY knows about this problem? I really need this fixed as soon as possible.

---

### Post by simpleeddie on 2009-11-01
Solution found!

Well, not really a solution, but more of a 'fix'.

First off, go into a terminal and type 'dmesg'

find the name of the device causing the lost interrupt, which in my case was 'ata6.01'

scroll up in the output and look for anything else above the first error that has the same name, and try and pinpoint the device it refers to (for me it was an old HP CD/DVD Drive).

All I did was turn my PC off and unplug the device, it was not needed and it completely solved my boot issues, 10 second boots are now a normal thing for me :D

thanks to [http://www.jimohalloran.com/2004/02/15/hda-lost-interrupt/](http://www.jimohalloran.com/2004/02/15/hda-lost-interrupt/) for helping turn the light on inside my head.

---

