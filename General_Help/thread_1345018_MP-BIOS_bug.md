---
title: "MP-BIOS bug"
date: 2009-12-03
forum: General Help
---

### Post by Rtech on 2009-12-03
Hello all. About time I got connected. I've been leaching off all the info I needed from the outside and for the most part have been able to solve a lot of issues I've had BUT I haven't been able to find squat on BIOS problems. Particularly: 

MP-BIOS bug: 8254 timer not connected to IO-API Kernal panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. then try booting with with the 'noapic' option

I've tried all options on the grub: 
Ubuntu 9.04, kernal 2.6.28-16-generic 
Ubuntu 9.04, kernal 2.6.28-16-generic (recovery mode)
Ubuntu 9.04, kernal 2.6.27-15-generic 
Ubuntu 9.04, kernal 2.6.27-17-generic (recovery mode)
Ubuntu 9.04, memtest86+

I'm dual booting with Vista(home premium 64bit) that came by default: Hp Pavilion Elie e9120y 
which has: An AMD Phemon II X4 910, ATI Radean HD 4350(512mb ded), 8G's of DDR3 RAM, 1 Tb of space, a,b,g,n Wireless Lan, Blue ray and a Super Multi DVD Burner. Nothing plugged in sept my tv(as the monitor) and mice/keyboard- All work fine.

I haven't done anything with the hardware nor have I touched the BOIS or the startup options. This is my none-experimental pc ;) 
This is VERY important that I can at least gain access to my files! I have my life portfolio on there. the sad things was I was just moving it to another HDD and making a copy to another external :[
Suspicions I have to why this accrued: I recently upgraded via network from Ubuntu 8.10 to 9.04 which worked with no problem(restarted the computer a couple times after the upgrade and it worked fine)

Help would be greatly appreciated!

---

### Post by dcstar on 2009-12-03
> **Rtech said:**
> Hello all. About time I got connected. I've been leaching off all the info I needed from the outside and for the most part have been able to solve a lot of issues I've had BUT I haven't been able to find squat on BIOS problems. Particularly: 

MP-BIOS bug: 8254 timer not connected to IO-API Kernal panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. then try booting with with the 'noapic' option

I've tried all options on the grub: 
Ubuntu 9.04, kernal 2.6.28-16-generic 
Ubuntu 9.04, kernal 2.6.28-16-generic (recovery mode)
Ubuntu 9.04, kernal 2.6.27-15-generic 
Ubuntu 9.04, kernal 2.6.27-17-generic (recovery mode)
Ubuntu 9.04, memtest86+

I'm dual booting with Vista(home premium 64bit) that came by default: Hp Pavilion Elie e9120y 
which has: An AMD Phemon II X4 910, ATI Radean HD 4350(512mb ded), 8G's of DDR3 RAM, 1 Tb of space, a,b,g,n Wireless Lan, Blue ray and a Super Multi DVD Burner. Nothing plugged in sept my tv(as the monitor) and mice/keyboard- All work fine.

I haven't done anything with the hardware nor have I touched the BOIS or the startup options. This is my none-experimental pc ;) 
This is VERY important that I can at least gain access to my files! I have my life portfolio on there. the sad things was I was just moving it to another HDD and making a copy to another external :[
Suspicions I have to why this accrued: I recently upgraded via network from Ubuntu 8.10 to 9.04 which worked with no problem(restarted the computer a couple times after the upgrade and it worked fine)

Help would be greatly appreciated!

Do you actually have a problem that is preventing you from using your Ubuntu system, or are you just complaining about a message that is having no material effect?

---

### Post by Rtech on 2009-12-04
O gotcha. Sorry. Yeah I forgot to mention that. It gets to the screen JUST before the login.. so the loading/splash screen and as soon as it it completes it distorts, like as if it changed to 16bit color.  then flashes an even more distorted figure of the splash screen (what I'd guess to be three times at the top of the screen) in a row of three, then goes black and freezes. I even tried putting it in safe graphics mode and I get the same thing.

---

### Post by Rtech on 2010-03-09
I ended up using the Ubuntu Live CD, recovered my files by mounting the hard drive then transferring my files to an external hard drive. I also deleted the old 32bit and now running 64bit :D In the end, my gut feeling was that the I had massive driver issues with my graphics card(ATI Radeon HD 4350) from goofing with the advance settings, something....I wont repeat ;)

---

