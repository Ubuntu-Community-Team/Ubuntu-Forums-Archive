---
title: "Request for driver help"
date: 2010-10-14
forum: General Help
---

### Post by elliottj on 2010-10-14
Hi all,
I am fairly familiar with Linux(for a noob), I've been on board since ubuntu 8.10, but I am not sure what to do about my problem. I had amazing performance with games on windows 7, and now that I'm on Meerkat, I get half of the fps. Also, My wireless range and speed is also about half of what it used to be. Is there anyone who would consider compiling drivers for me, or maybe even pointing me in the right direction to get this solved? ANY help would be greatly appreciated. I have dual booted for a long time, but this is the first time im pure ubuntu, and I'm planning on keeping it that way. Thanks again for any help guys!!!!!

Wireless N adapter:

06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

ATI Radeon graphics:

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]

My laptop is the Acer Aspire 4451

---

### Post by Mark Phelps on 2010-10-14
Are you already running the proprietary AMD drivers? If you don't know for sure, open a terminal and enter "fglrxinfo".  If you get something like "command not found", you're running the open-source drivers.  In that case, go to Hardware Additions (I think that's the name in 10.10) and see if you are offered proprietary drivers.

---

### Post by elliottj on 2010-10-14
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10237 Compatibility Profile Context


I did download the proprietary drivers manually, but is that really as good as it gets? or is there maybe just more customizing I need to do?

---

