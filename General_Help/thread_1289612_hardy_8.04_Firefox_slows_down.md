---
title: "hardy 8.04 Firefox slows down"
date: 2009-10-12
forum: General Help
---

### Post by charonred on 2009-10-12
Several apps slow down for no reason - Firefox is the main one, it just 'greys' out and becomes unresponsive for 10 - 30 seconds; and this still happens after my recent CPU upgrade.

The board is a Gigabyte MA790FX-DS5, and just last week I replaced the 2.8 Ghz Athlon X2 with a 3.0 Ghz Phenom 945 X4; and I have 4GB of Kingston HyperX RAM @1066 Mhz, but the system still bogs down from time to time.

The strange thing is that while it 'bogs' down, the CPU meter typically shows 1%, 5%, 2%, 7% type results for individual cores, so it's not like the CPU is being over-worked; and memory usage is typically about the 20% - 25% region.

So what gives :confused:

---

### Post by RedRat on 2009-10-12
You might want to check how much cache memory you have allocated. I believe the default is 20Mb or 50Mb. If you are downloading large pictures for example, it will gray out on you for some time. Increasing the cache to 100Mb or 200mb helped the situation on my computer. It still does this but usually clears in about 15 seconds, particularly since I use BatchDownload and have quite a few downloads selected.

---

### Post by PrePenguin on 2009-10-12
Are you using the 64 bit version? Thats if thats version even has a 64 bit version..

---

### Post by charonred on 2009-10-12
not downloading anything sometimes when it 'greys' out, maybe typing an email or opening another app

32 bit version; though I'm thinking of going 64 bit soon; either Hardy 8.04 or Karmic 9.10 when it comes out - then I'll double the memory too.

---

### Post by RedRat on 2009-10-12
One other thing to check, I initially had this problem and posted here about it. What i found eventually was that for reasons unknown to me, my monitor settings in nvida-settings was set for a scan rate of 50Hz. Firefox would actually crash. Now why this should happen is beyond me and I never got an answer. But by setting the scan rate to 60Hz, this cleared the problem. You might want to ensure that your monitor scan rates are correct for your monitor. May or may not help your cause, I am kinda guessing in the dark here.

---

### Post by charonred on 2009-10-12
I have 2 Samsung SyncMaster 943N monitors each @ 1280 x 1024 resolution, but running together as one big desktop @ 2560 x 1024; monitors have a max refresh rate of 75 Hz.

The CCC for the ATI Radeon 3450 card is set to 60 Hz for each monitor; one connector is VGA, the other is HDMI with VGA adaptor - but I had same problem with previous Radeon 2600 Pro which had 2 x VGA connectors, so don't think that affects it. Card has 512 MB DDR2 memory, with memory clock of 400 MHz and Core clock of 600 MHz - PCIe 2.0 x 16

Generally Thunderbird occupies one monitor, with Firefox the other; plus any other apps I'm running at the time; ditto for 2nd Desk. 

I'm also using Compiz with Emerald as decorator, and have 3D cube etc enabled.

---

### Post by RedRat on 2009-10-12
From what you describe, going to the 64bit version may help. I really think you have adequate memory, 4Gb, and your processor is good. The only thing I can say is perhaps it is a problem of the video card and drivers (yes, I know that this is a great fall back in the Linux world). 

Maybe, instead of adding more system memory, you might want to invest in a 'better' card/driver combo. I use an Nvidia card (9600GT) and my driver is even a bit old, not the latest, but I don't have the extreme conditions you describe.

---

### Post by charonred on 2009-10-12
I'd been thinking of spending a bit more on a new Video card sometime; but as the PC just got a new CPU, and I have some upcoming m/bike expenses, plus the need to update to a later model car, the video card simply has to go on the back-burner for a while - $$$ only go so far; the additional memory will cost about AUD$100 (about the same as existing card), whereas a newer/better card may be around $250+.

So for the moment just need any advice on how to tweak settings to sort problem out as much as possible (and go 64 bit at end of month).

---

### Post by lovinglinux on 2009-10-13
See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

