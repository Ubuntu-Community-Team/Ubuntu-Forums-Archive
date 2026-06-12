---
title: "Frequent crashing of Lucid Lynx"
date: 2010-05-05
forum: General Help
---

### Post by Andreas_D on 2010-05-05
Hi there,


since having installed Lucid Lynx, I have several complete system crashes a day, no matter which applications I am using. Lucid crashes without any error message and the system reboots.
I have had no problem whatsoever with Karmic Koala (also switched from ext2 to ext4 when installing Lucid Lynx).
Is there any probable reason for that or a workaround? Can I paste any logs here for anybody to figure out what might be going on?
When I try XP which is also install, the system won't crash (so far...), so I don't think it's a hardware problem.

Anyhow, thanks a lot!
Andy


My system:

[LIST]
[*] Mainboard: Gigabyte GA-MA78G-DS3H, AMD 780G, ATX
[*][FONT=monospace] Processor: [/FONT]AMD Athlon64 X2 4800+ AM2 box "EE" 65W, 2x512kB
[*]Coolermaster Centurion5 Schw. CAC-T05-UW ohne Netzteil
[*]ATX BE Quiet! Straight Power 400 Watt / BQT E5
[*]2x2048MB DDR2 Aeneon PC6400 CL 5, PC6400/800
[*]DVD: LG GH20N bare schwarz (SATA-II)
[*]HDD: Seagate Barracuda 7200.11 500GB SATA II ST3500320AS
[/LIST]

---

### Post by dino99 on 2010-05-05
when a system often have this kind of issue you might think about too high temperatures , fans not working or dusty system

you may have errors logged into 
.Xsession-errors ( into /home, its a hidden file by default, so check the menu to unhide the file first, to see it)

or into : system admin log viewer

---

### Post by Andreas_D on 2010-05-05
Thanks dino,

am quite scrupulous with fanning my PC. :-)

Does

    andy@andy-desktop:/$ sensors
    k8temp-pci-00c3
    Adapter: PCI adapter
    Core0 Temp:  +26.0°C                                    
    Core0 Temp:  +17.0°C                                    
    Core1 Temp:  +23.0°C                                    
    Core1 Temp:  +19.0°C 

look as if there's a problem?

Andy

---

### Post by utnubuuser on 2010-05-05
Getting the same issue.

Had it since alpha.  

System randomly crashes, or rather, the xserver seems to crash, because the machine doesn't go down completely, - likewise, no error messages -  instead, the screen goes black and flashes a bunch of vertical stripes every 4-5 seconds.  have to actually restart with ctrl+alt+del
This is now a system upgraded from 8.04 to 10.04 - intel with intel onboard though I was having the same problem when installed fresh from cd.

the only noteworthy consistency seemed to be in firefox, that, whenever I tried to enter a search in the search-box, the system went down. -Got around that by removing the search-box, then placing it in the top row of firefox window instead of second row.

---

### Post by snaildarter on 2010-05-24
Same here.  Things worked fine before.  System upgraded from 8.04 to 10.04.  Crashes a lot, but most consistently when opening a new window or program.  Not a complete hardware lockup, but screen goes crazy.  Intel graphics, but not using any 3d effects.  Seems to possibly be associated with anything that spikes the CPU; again, like opening a window or program.  I don't know how to diagnose such a problem.

I can watch mythtv for hours (~50% cpu), then simply open the home folder or Chromium or anything and bam, jumbled screen and lockup.

---

