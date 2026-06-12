---
title: "USB ports stopped working"
date: 2009-12-27
forum: General Help
---

### Post by minimustangs on 2009-12-27
Hmmm, i thought I posted a thread about this earlier today, but can't find it, so pardon me if it's repetitive...

For some unexplained reason, today all my USB devices will not work. My mouse will blink on and off a few times, but in the end it remains inactive. My USB keyboard doesn't function at all. Flash drives blink but are not recognized by the system. All was working fine first thing this morning - the only think=g out of the ordinary were some system updates.

Laptop is a ACER Aspire 5100 series.

Thanks,

Steve

Oh, btw DMESG output:

42.852079] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?

---

### Post by dcstar on 2009-12-27
> **minimustangs said:**
> Hmmm, i thought I posted a thread about this earlier today, but can't find it, so pardon me if it's repetitive...

For some unexplained reason, today all my USB devices will not work. My mouse will blink on and off a few times, but in the end it remains inactive. My USB keyboard doesn't function at all. Flash drives blink but are not recognized by the system. All was working fine first thing this morning - the only think=g out of the ordinary were some system updates.

Laptop is a ACER Aspire 5100 series.

Thanks,

Steve

Oh, btw DMESG output:

42.852079] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?

Totally power off and see if things work when restarted (you may also have to remove the battery).

---

### Post by minimustangs on 2009-12-27
Heh....Powered it off several times already today, with and without h/w attached. Didn't think to remove battery though. Will try that now. Stay tuned...

o.k....

popped battery out, even left system unplugged for a few minutes, still the same....USB not working.

Additionally, while the screen is showing the partition Ubuntu is being loaded from the mouse blinks once. A bit later in the boot cycle it blinks on and of, maybe 7 times. Hard to get an accurate # snce it happens so fast.

---

### Post by minimustangs on 2009-12-28
Well because I can't leave well enough alone, I booted my laptop up with Knoppix 3.8, let it do the AUTO config. It says USB detected and goes on it's merry way. Mouse still not working. I can't remember if there were things I needed to do in Knoppix to enable the USB mouse instead of the touchpad. 

At any rate, ports ( all three ) not working...

OUTPUT of LSUSB , LSMOD....

$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ lsmod | grep rt
parport                35340  2 ppdev,lp
agpgart                34988  3 ttm,drm,ati_agp

---

### Post by minimustangs on 2009-12-29
Just updating that USB ports are completely NOT WORKING. Not even slow. Just not working. I hate to think I need to wipe my system to investigate if it's a s/w bug that can eventually be corrected. Until this struck me two days ago, everything was working pretty much without issue.

---

### Post by khelben1979 on 2009-12-30
It sounds to me that the laptop itself needs to get repaired. I think it's a hardware problem.

---

