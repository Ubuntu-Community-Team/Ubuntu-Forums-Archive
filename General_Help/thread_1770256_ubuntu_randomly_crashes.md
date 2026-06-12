---
title: "ubuntu randomly crashes"
date: 2011-05-29
forum: General Help
---

### Post by cllewis91592 on 2011-05-29
im using 11.04 and at random times it will crash. it shows alot of text on the screen and at the bottom it says something to the effect of "panic, reverting to text" or something like that. but when it crashes i cant do anything, mouse,keyboard,everything  stops working and i need to restart my computer. 



thanks for the help!

---

### Post by wildmanne39 on 2011-05-29
> **cllewis91592 said:**
> im using 11.04 and at random times it will crash. it shows alot of text on the screen and at the bottom it says something to the effect of "panic, reverting to text" or something like that. but when it crashes i cant do anything, mouse,keyboard,everything  stops working and i need to restart my computer. 



thanks for the help!Hi we need to know what your are doing when this happens? what are your system specs? How old is your system? Laptop or desktop?Are you using the cube or effects?Put this into a terminal
```
lspci
```
and post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by cllewis91592 on 2011-05-29
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```when it crashes im doing normal things like surfing the net. last time it happened i was watching a video on youtube,but it does not happen every time i go on youtube. any thoughts? also im not using any desktop effects and it is a new laptop, it is a compaq presario CQ62 if that helps.

---

### Post by wildmanne39 on 2011-05-29
> **cllewis91592 said:**
> ```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```when it crashes im doing normal things like surfing the net. last time it happened i was watching a video on youtube,but it does not happen every time i go on youtube. any thoughts? also im not using any desktop effects and it is a new laptop, it is a compaq presario CQ62 if that helps.
Hi, there is some problems with the intel graphic cards not working just right with ubuntu,did you look in additional drivers to see if there is a driver for your video card there? I do not think there is but it does not hurt to look. It is also possible that the flash in firefox is causing problems, you can open firefox click on addons and install flash aid it will fix flash for you just follow the on screen instructions. Can you get the unity desktop with the launcher on the left side of the screen?

---

### Post by cllewis91592 on 2011-05-29
> **wildmanne39 said:**
> Hi, there is some problems with the intel graphic cards not working just right with ubuntu,did you look in additional drivers to see if there is a driver for your video card there? I do not think there is but it does not hurt to look. It is also possible that the flash in firefox is causing problems, you can open firefox click on addons and install flash aid it will fix flash for you just follow the on screen instructions. Can you get the unity desktop with the launcher on the left side of the screen?
i installed flash aid and i will see if it helps and check back in later, however it crashed about 10 minuets ago while i was in the software center. i wish i could get a screenshot of it, but sadly as i said i can't do anything when it happens. also there was no other drivers available.

---

### Post by wildmanne39 on 2011-05-29
> **cllewis91592 said:**
> i installed flash aid and i will see if it helps and check back in later, however it crashed about 10 minuets ago while i was in the software center. i wish i could get a screenshot of it, but sadly as i said i can't do anything when it happens. also there was no other drivers available.Hi, you can go to administration and click on log file viewer and check out the logs in there but there are many and quite long.

---

### Post by cllewis91592 on 2011-05-29
> **wildmanne39 said:**
> Hi, you can go to administration and click on log file viewer and check out the logs in there but there are many and quite long.
i looked through the log files and couldn't find anything that had the only line of text i saw last time it crashed, and im sure nobody wants me to post all the log files here. but it hasn't crashed in awhile, fingers crossed!

---

### Post by wildmanne39 on 2011-05-29
> **cllewis91592 said:**
> i looked through the log files and couldn't find anything that had the only line of text i saw last time it crashed, and im sure nobody wants me to post all the log files here. but it hasn't crashed in awhile, fingers crossed!
Hi, good luck some people have this issue and have not be able to fix it.

---

### Post by cllewis91592 on 2011-05-29
> **wildmanne39 said:**
> Hi, good luck some people have this issue and have not be able to fix it.
its been almost 3 hours since the last crash, maybe the flash aid fixed it :)

---

### Post by Topsiho on 2011-05-29
Maybe it's not software, but hardware.

You could try and check the ram (internal, working memory) in your computer with memtest (on your livecd). You say your computer is new, that doesn't mean that the hardware is OK (sadly).

Topsiho

---

### Post by cllewis91592 on 2011-05-29
i just had a thought, could it be an over heating issue? i noticed it crashed when it was fairly warm. i try to keep it cool but when i leave it flat for awhile it gets hot. although it didn't feel like it was over heated but maybe i have a hardware error :confused:

i will do a test to see if that is it, worth a shot.

---

### Post by wildmanne39 on 2011-05-29
> **cllewis91592 said:**
> i just had a thought, could it be an over heating issue? i noticed it crashed when it was fairly warm. i try to keep it cool but when i leave it flat for awhile it gets hot. although it didn't feel like it was over heated but maybe i have a hardware error :confused:

i will do a test to see if that is it, worth a shot.Hi, yes it could be that is one reason I was asking about your hardware specs, laptops get a lot hotter then desktops, I use a cooling pad under mine to help keep it cool,also it need to be on a board so the fan is not covered up on the bottom.

---

### Post by cllewis91592 on 2011-05-29
> **wildmanne39 said:**
> Hi, yes it could be that is one reason I was asking about your hardware specs, laptops get a lot hotter then desktops, I use a cooling pad under mine to help keep it cool,also it need to be on a board so the fan is not covered up on the bottom.
do you know a way i could edit the fan speed to make it stay cool, or would that make it run hotter? also i think i have confirmed the overheat issue, when it heats up and cools down is when it crashes,but i could be wrong.

---

### Post by wildmanne39 on 2011-05-29
> **cllewis91592 said:**
> do you know a way i could edit the fan speed to make it stay cool, or would that make it run hotter? also i think i have confirmed the overheat issue, when it heats up and cools down is when it crashes,but i could be wrong.

Hi, when it is under a load do you hear the fan speed up? if so I would not adjust it, there is a way but I do not know it. Make sure you keep it on like a cutting board that is what I use for mine so it can get air from the bottom through the fan, also you should invest twenty dollars a get a cooling pad. I also noticed that when I play shows from hulu in full screen mode my desktop heats up a lot.

---

### Post by linuxinstalledfromhdd on 2011-05-29
> **cllewis91592 said:**
> do you know a way i could edit the fan speed to make it stay cool, or would that make it run hotter? also i think i have confirmed the overheat issue, when it heats up and cools down is when it crashes,but i could be wrong.

There is an alternative way to test your hardware. Create a Live Bootable Stick of Ubuntu 10.10 made with "persistance", and use the Startup Disc Creator to put it on your USB Flash device.  Boot from that newly created live Ubuntu USB stick.

Leave it in the unit and monitor if there are any significant changes in behaviour. If it is a hardware issue, you will have at least eliminated the OS as being the culprit. It's a process of elimination to figure out hardware issues.

---

### Post by cllewis91592 on 2011-05-29
> **wildmanne39 said:**
> Hi, when it is under a load do you hear the fan speed up? if so I would not adjust it, there is a way but I do not know it. Make sure you keep it on like a cutting board that is what I use for mine so it can get air from the bottom through the fan, also you should invest twenty dollars a get a cooling pad. I also noticed that when I play shows from hulu in full screen mode my desktop heats up a lot.
i went out and bought a cheap cooling mat,maybe it will help.

---

### Post by wildmanne39 on 2011-05-29
> **cllewis91592 said:**
> i went out and bought a cheap cooling mat,maybe it will help.Hi, thats good, even if it does not fix the problem it will keep the computer cooler and it will run faster and last a lot longer.

---

### Post by Topsiho on 2011-05-30
If the notebook gets too hot, why not return it to the shop where you bought it from? A computer that gets too hot and even crashes is quite useless, and ends up as a door stopper or very expensive paper weight. You said it was a new notebook. It might even be dangerous to use as it might be a fire hazard.

Can you measure the temperature, as a function of load and time.
You might try and install lm-sensors if that's not done already, from synaptic or with: sudo apt-get install lm-sensors , in a terminal.

Topsiho

---

