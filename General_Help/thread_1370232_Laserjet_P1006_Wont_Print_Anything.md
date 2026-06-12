---
title: "Laserjet P1006 Wont Print Anything"
date: 2010-01-02
forum: General Help
---

### Post by falcon1620 on 2010-01-02
Hi everyone,
   My printer, previously working now will not print anything and I can't figure out what's going on. I have tried several times to install the printer, and run through the gauntlet of settings here with 9.10 here. I have enen tried to run thought the setup for this printer straight from the HPLIP directly. I have given up on this and now I have reverted to a fresh install of 9.10, with the settings that are default to having plugged in the printer. I ran through the HP console set up here that was presented after Ubuntu searched for some drivers. I have just been using the previous version of Ubuntu with this printer and for some reason the new version isn't working. It doesn't even identify that it has a job for processing, it sits idle and when submited jobs it just sits no blinking or anything not even a hint of a printout. I'm getting desperate here trying to square away some TAX forums for business.

Here are some settings from CUPS on this machine. 

Description:	HP LaserJet P1006
Location:	
Driver:	HP LaserJet P1006 Foomatic/foo2xqx (recommended) (grayscale, 2-sided printing)
Connection:	hp:/usb/HP_LaserJet_P1006?serial=AC18FZQ
Defaults:	job-sheets=none, none media=na_letter_8.5x11in sides=one-sided

I sent the following jobs
	Name	User	Size	Pages	State	Control
HP-LaserJet-P1006-6  	Test Page  	falcon  	150k  	1  	completed at
Fri 01 Jan 2010 11:02:45 PM MST  	 
HP-LaserJet-P1006-5  	Test Page  	falcon  	1k  	Unknown  	completed at
Fri 01 Jan 2010 11:02:18 PM MST  	 
HP-LaserJet-P1006-4  	Test Page  	falcon  	1k  	Unknown  	completed at
Fri 01 Jan 2010 11:01:57 PM MST  	 
HP-LaserJet-P1006-3  	Test Page  	falcon  	150k  	2  	completed at
Fri 01 Jan 2010 11:05:09 PM MST  	 
HP-LaserJet-P1006-2  	Test Page  	falcon  	1k  	Unknown  	completed at
Fri 01 Jan 2010 10:53:12 PM MST  	 
HP-LaserJet-P1006-1  	Test Page  	falcon  	150k  	1  	completed at
Fri 01 Jan 2010 10:52:14 PM MST 

and not a single one of them printed. In fact no blinky lights either... So my question is if the jobs are reported "complete" but I don't get them where would they be? 

Oh I have also tried adding the printer as HP_LaserJet_P1006	HP LaserJet P1006		HP LaserJet p1006 hpijs, 3.9.8	Idle - "/usr/lib/cups/filter/foomatic-rip failed" but as you can see the status of that device fails.... 

Do you have and Ideas? Thanks... Other than that loving 9.10! :)

---

### Post by falcon1620 on 2010-01-07
The latest update to CUPS 1.4.1 under 9.10 seemed to resolve my printing issue. It now prompts for a plugin download and prints from the printer HORRAY!!! I can now nix Vista again. :D

---

