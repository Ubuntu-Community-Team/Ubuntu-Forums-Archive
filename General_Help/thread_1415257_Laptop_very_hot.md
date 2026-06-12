---
title: "Laptop very hot"
date: 2010-02-24
forum: General Help
---

### Post by drdanielfc on 2010-02-24
Hello everybody,
  This has been a problem for a while now but I just decided to get around to fixing it. My laptop has been getting very hot under Ubuntu, much hotter than it was recently. I can rule out dust, etc because this problem seemed to occur all at once. Powertop reports the following:
```
     PowerTOP version 1.11      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.9%)         1.84 Ghz     0.0%
polling           0.0ms ( 0.0%)         1333 Mhz     0.0%
C1 halt           0.0ms ( 0.0%)         1000 Mhz   100.0%
C2                1.1ms (95.1%)


Wakeups-from-idle per second : 884.5    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  39.0% (428.4)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  11.3% (123.6)       <interrupt> : extra timer interrupt 
  10.8% (118.8)   chromium-browse : hrtimer_start_range_ns (hrtimer_wakeup) 
   9.4% (102.8)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   7.8% ( 85.8)       <interrupt> : ehci_hcd:usb1, uhci_hcd:usb2 
   7.6% ( 84.0)   USB device 1-3.1 : Mass Storage Device (Generic) 

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

 Q - Quit   R - Refresh   U - Enable USB suspend 

```

According to System Monitor, my CPU usage is only about 10% for each processor, and the load avarages dont go above 0.25. Here are my system specs: 
```
--HP's Compaq nx9420--
Intel Core Duo processor T2400 (1.83-GHz, 667-MHz FSB, 2-MB L2 cache)
17.0-inch WSXGA+ wide viewing angle BrightView display with 1680 x 1050 resolution and 16M colors
1GB (1x1GB) 533-MHz DDR2 SDRAM
ATI Mobility Radeon X1600 graphics controller with 256 MB of discrete video memory
100GB 5400RPM Hard Disk Drive
Built-In Intel PRO/Wireless 3945 A/B/G
HP Integrated Module with Bluetooth 2.0 Wireless Technology
8-cell high capacity Lithium-Ion (68Wh)
DVD+/-RW SuperMulti with Double Layer
Ports: 1x IEEE 1394a Port, 1x Type I/II PC card slot, 1x S-Video TV out, 1x VGA/External Monitor, 1x 7-in-1 Media Reader, 4x USB 2.0, 1x headphone out, 1x microphone in
Security features include integrated Smart Card Reader, TPM Embedded Security Chip, and Biometric Fingerprint Sensor
Comes with Windows XP Professional
Dimensions: 1.3 in (at front) x 15.5 in x 10.8 in (33 mm x 393 mm x 275 mm)
Weight: 7.4lb (3.36kg)
```

Im worried that its my ATI driver because it seems ati has dropped fglrx support for the x1600, and i cannot get it to install properly (radeon works fine but i tried fglrx to see if it would solve my overheating problem). I have read some threads that say to fix the problem I should set my powerstate to 1, but i cannot do so without fglrx:frown: Ill do anything (except windows blegh) to get the laptop to stop overheating all I wish is to be able to get some work done without my lap catching on fire.

---

### Post by drdanielfc on 2010-02-24
bump :(

---

### Post by drdanielfc on 2010-02-24
bump

---

### Post by QIII on 2010-02-24
Unfortunately, AMD/ATI has "legacied" you.


> AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.


Your only choice will likely be the radeon open source driver.

How old is the machine itself?

(As an aside, don't bump so quickly.  You may get your wrist slapped.  A 24 hour bump is more acceptable.)

---

### Post by drdanielfc on 2010-02-24
> **QIII said:**
> Unfortunately, AMD/ATI has "legacied" you.





Your only choice will likely be the radeon open source driver.

How old is the machine itself?

(As an aside, don't bump so quickly.  You may get your wrist slapped.  A 24 hour bump is more acceptable.)

Sorry for the bumps, and yes the machine is fairly old, at least 4 years. Is it possible I could run an older version of ubuntu?

---

### Post by QIII on 2010-02-24
8.04 is an LTS version.  It will be supported until April, 2011.  Catalyst 9.8 might work with that.

Not convinced that is your overheating problem, though.  Could be any number of things -- battery getting old, cooling fan bushings binding, baked thermal compound between processor and cooling system.

You might try to install some sensors and keep track of your CPU temperature specifically.  If the thermal compound has broken down, you won't get good head transfer off the CPU and the cooling system will not work well.

---

### Post by drdanielfc on 2010-02-25
> **QIII said:**
> 8.04 is an LTS version.  It will be supported until April, 2011.  Catalyst 9.8 might work with that.

Not convinced that is your overheating problem, though.  Could be any number of things -- battery getting old, cooling fan bushings binding, baked thermal compound between processor and cooling system.

You might try to install some sensors and keep track of your CPU temperature specifically.  If the thermal compound has broken down, you won't get good head transfer off the CPU and the cooling system will not work well.

thanks i tried fglrx in hardy and the laptop went into overkill. then i put the powerstate to 1 and it seems to be getting better but gtg school rite now

---

### Post by drdanielfc on 2010-02-25
Solved :p.

For anyone else who has this problem, here was my solution:

1. Downgrade to hardy (unfortunate, but what am I gonna do?)
2. Install fglrx via Hardware Drivers
3. Reboot
4. Install all updates
5. Add *aticonfig --set-powerstate=1* to startup applications (sessions)
6. Reboot a final time :-)

Note: After bootup the fan seems to rev up for about 3 minutes and then it quiets down, I assume this is because it takes the driver a second to figure out that it needs to slow itself down

Note: If you dont set the powerstate to 1, the laptop actually feels even hotter than before

---

