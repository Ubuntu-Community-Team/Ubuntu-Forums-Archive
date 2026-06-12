---
title: "Multiple Boot attempts before successful boot."
date: 2010-10-22
forum: General Help
---

### Post by noo2buntu on 2010-10-22
I'm not sure if this is the correct place to raise this issue but here goes.

I'm using Ubuntu Maverick which seems to run ok. The problem is when booting my PC. Often it takes anywhere between two and six attempts to boot before a successful boot. Sometimes it fails with "No signal" before it reaches the grub screen, sometimes is passes grub only to fail 15 secs later with a "No signal".

I have an NVidia Ge Force 6600 LE graphics card, with the latest driver 260.19.06.

Any advice would be greatly appreciated.
:(

---

### Post by blueridgedog on 2010-10-22
Have you determined if it is actually booting, but you just can't see it?  Failures before grub are likely hardware related (bios, graphics card etc).  If you leave it, will it play the drum sound indicating a boot?

---

### Post by noo2buntu on 2010-10-22
Irrespective of the stage the boot process has reached the red light associated with disk access is flashing and there is the normal fan noise. I've tried leaving it to see if it eventually boots up but it doesn't.

Have also performed 'smart' hdd check and everything is reported ok.

It's worth mentioning that when it has booted up normally and I do a re-start it usually boots up normally (but not always). When I boot up first thing in the morning that is when it can take up to six attempts.

Thanks for looking.

---

### Post by blueridgedog on 2010-10-23
The hard drive activity indicates that it is booting normally and the issue is the signal to the monitor.  Since this happens at time before grub, it is probably not an os issue.  Is your monitor left on all the time?  When it occurs, have you tried unplugging and replugging the monitor cable?  How about power cycling the monitor?  Do you have an add on graphics card and a built in graphics device (two monitor ports?).

---

### Post by noo2buntu on 2010-10-23
Many thanks for giving this some thought and suggestions.

I've just rebooted and it didn't fail at until the fifth attempt (wouldn't you just know it!!) When it did eventually fail I tried power cycling the monitor but it didn't make any difference.

I have an Nvidia graphics card and on board graphics ie two graphic ports. 

The entire Pc and peripherals are all switched off overnight.

Tomorrow morning when I can be sure the boot process will fail to display I will try booting with and without the graphics card; disconnect the monitor from the PC and reconnect and see what happens.

---

### Post by blueridgedog on 2010-10-23
Also, when it acts up, try plugging in the monitor to the onboard port...just to test if it is being activated by the bios.

---

### Post by noo2buntu on 2010-10-27
I did as you suggested but there was no difference.

In the end I disconnected the hard drive and booted up - it failed so after all that it was the motherboard. I've since replaced it and everything is now working as it should be:)

Interestingly the new motherboard has resurrected an old hard drive which I left in there (disconnected of course). Strange how these problems manifest them selves.

Anyway thanks for your time and suggestions.

Kind regards

---

