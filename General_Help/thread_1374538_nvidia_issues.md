---
title: "nvidia issues"
date: 2010-01-06
forum: General Help
---

### Post by ronniestamps on 2010-01-06
First of all, thank you to every single contributor! If it were not for Ubuntu, I would not be windoze free. Not only am I windoze free, but my entire family has now been windoze free for a year now, which is HUGE considering their computer skill level - NONE. THANK YOU ALL!

I recently upgraded to 9.10 from 8.10 and my dual monitor setup stopped working. I have a GeForce FX5200 utilizing dual monitors. I tackled the problem last year and only remembered that the issue was within xorg.conf. So basically, I was at square one again... with the worse timing possible. I had multiple projects due for school, a website deadline, and a private investigator that needed some data recovered in a high profile criminal case. 

Cutting to the chase... there are a ton of issues revolving around nvidia drivers, with an equal amount of solutions. My issue was that when I would set my bios to use the pci graphics card, Ubuntu would not boot. It would hang right after grub, with a black screen, until a key press, then would display cryptic info. Basically, it could not load anything. Then when I'd switch back to onboard graphics, it would boot into low graphics mode. NOTE: if I tried to install a fresh copy from scratch, with bios set to pci graphics, it failed at the partitioning stage. 

What it boiled down to was an addressing issue. (I'm self-taught, so some of my terms are a little off, sorry) So, the fix:

If you are able to load Ubuntu in low graphics mode, open a terminal and type **lspci**. This will give you all of the ACTUAL pci addresses. Write down the address for your graphics card, it should be something like: **02:05.0** (the number after the last dot is insignificant for these purposes, only the colon numbers matter). Then type **sudo gedit /etc/X11/xorg.conf** or which ever command you'd use to open that file with su/root privledges. Under the Section "Device" add this line: **BusID "PCI:02:05". **Save, Reboot. Change your bios to pci graphics if that's the case for you. Once rebooted and logged in, you can open nvidia settings and configure your settings. 

Basically, the reason "no devices found" is because Ubuntu is looking in the wrong place. It either has the wrong address or no address at all. (If anyone more qualified than myself is reading this, please clarify for everyone) I tried EVERY solution, and none of them worked for me. Not because they were wrong, just not applicable to my issue. If anyone wants or needs my hardware/software specifics, let me know.... I need to get back to work, just wanted to get this info out there.

BTW, for older graphics cards, DO NOT use the new nvidia drivers, they will reek havoc on your system and leave broken packages on your system!

Ronnie

---

