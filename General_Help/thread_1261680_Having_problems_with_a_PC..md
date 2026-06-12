---
title: "Having problems with a PC."
date: 2009-09-09
forum: General Help
---

### Post by briantoumbs on 2009-09-09
Recently my computer stopped booting. It would go from the dell splash screen saying I can push F2 for setup and F12 for something else, to a black screen with a flashing white dash.

I tried to push F2 at startup but it goes straight to the black screen.. Not allowing me to get to the bios.

I then removed the hard drive and plugged it in a different pc and was able to retrieve the data on it., meanwhile I tried to boot the pc again, this time with out a hard drive i was able to get into the bios. I switched it to boot from a cd first and put in a live cd of Ubuntu. After rebooting it loaded Ubuntu - it has been running for a few days straight on the live cd - I attempted to re-connect the hard drive sense it appeared to be working, with out changing bios settings to boot from the hard drive first, so it should boot from cd an load linux, yet it went straight to a black screen. took the hard drive off again and tried to boot the live cd again, it took a few restarts then booted been running on the live cd for a few weeks now. 


I removed the cmos battery and put it back in, reseting the bios, when it booted it said somehting about the setting the date and time and then somehting about low voltage or power on the battery..



Could it be the cmos battery?? or would a bad hard drive cause the pc not to boot even when it is set to boot from a cd first? I am completely confused at this point.

---

### Post by Exodist on 2009-09-09
CMOS battery is only used to store your BIOS information while the PC is off. When your PC is own, its just sitting there. 

Your black screen could be caused by a number of things. 
If HDD was down the BIOS would complain about nothing to boot from.
If you video was down you wouldnt see the black screen with a Courser blinking.
If you RAM went bad, you PC prob wouldnt boot and just beep at you. Also video may do this sometimes also.

But if you BIOS is shot, you should just get a black screen.

Try reflashing your BIOS if thats possible, but I doubt ita let you boot from floppy to even do that. You may have to see a PC shop if any around where you live has a BIOS chip reader.

- Exo

---

### Post by briantoumbs on 2009-09-09
If its running off 9.04s live cd would the bios still be bad. Thats the part I dont understand. I could see if it wouldn't boot to the live cd. But it works perfectly.

---

### Post by Carondimonio on 2009-09-09
Which OS is on the HDD?

In any case, I would say it's a bad MBR or some damaged file which is called right at start-up.

---

### Post by Firestem4 on 2009-09-09
If your system can boot to a LiveCD (regardless of the HDD issue) then the BIOS is working. The primary function that the bios performs for the pc is booting the system and finding the bootloader for the OS. After that Linux takes over. (Windows actively uses the BIOS for system clock and etc whereas Linux does not).

Depending on how old the computer is you may need to replace the CMOS battery. Typically they last around 5 years, though this is debatable  since I personally have seen dead batteries on 1 year old machines, or fine batteries on 10 year old machines.

There is no need to reflash the bios. Chances are it could be a bad cable (power or data) somewhere on the system. I had a bad RAM module that acted as a shunt after my motherboard killed the RAM chip. it caused the system not to boot.

---

### Post by Exodist on 2009-09-09
> **briantoumbs said:**
> If its running off 9.04s live cd would the bios still be bad. Thats the part I dont understand. I could see if it wouldn't boot to the live cd. But it works perfectly.

Like stated above. If you booting off Live CD your BIOS is working fine.

You may be having a HDD quirk tho. Check your BIOS settings tho to make sure that its set to boot off a hard drive also. It is possible the MBR has got corrupted. But to be honest its hard to tell without seeing whats going on first hand for me.. :-(

---

### Post by Icehuck on 2009-09-09
Do you have a flash drive plugged in? I've had a few Dell machines behave exactly the same way and when the flash drive was removed it booted fine.

---

### Post by lisati on 2009-09-09
> **Firestem4 said:**
> If your system can boot to a LiveCD (regardless of the HDD issue) then the BIOS is working. The primary function that the bios performs for the pc is booting the system and finding the bootloader for the OS. After that Linux takes over. (Windows actively uses the BIOS for system clock and etc whereas Linux does not).

+1
You might want to think of the BIOS as a set of "helper" programs built into the computer that are used to get the computer started, and which aren't always needed once the operating system is up and running. (To what extents they're not needed can depend on the OS and whatever drivers it loads)

Running off the LiveCD also suggests that the display system (a possible cause of the "blank screen and flashing cursor" situation) is also usable.

---

### Post by Warpnow on 2009-09-09
I once had a hard drive that when was plugged in, the motherboard did not seem to get power. No lights. Unplug it, and power returned.

To this day I cannot explain it. I think some errors are down to electricity and engineering on a level very few people understand, and I'm certainly not one of them.

---

### Post by briantoumbs on 2009-09-09
I have been kind of thinking it has to do with the hard drive, but I think I will go out and get a new cmos battery. Only extra one I had is from a pc thats about 10 years older than the one thats broke.

---

### Post by GoldenSun on 2009-09-09
> **briantoumbs said:**
> I have been kind of thinking it has to do with the hard drive, but I think I will go out and get a new cmos battery. Only extra one I had is from a pc thats about 10 years older than the one thats broke.

No need to get cmos battery if the bios saves your settings.  I have never replaced a cmos battery, and I still use a dell r400 (10 years old) on DSL.  

Have you hooked the hd up to another computer and tried to boot form it.  (Sorry if you have done this but I didn't feel like reading through the entire thread).  You could also hook up a different hd with a os installed and try to boot from that on the non-working computer.  

I would burn a memtest86 on a cd and run that for a little while to test ram.

---

