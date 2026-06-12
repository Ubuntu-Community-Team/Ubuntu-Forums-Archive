---
title: "Ubuntu Freezes 'Randomly'"
date: 2010-08-20
forum: General Help
---

### Post by chinggisk on 2010-08-20
Hello all,

I am a total Linux noob who just built a new system and decided to load the 10.04 64-bit version of Ubuntu on it.  Since I've got everything up and running, however, I keep getting seemingly random system freezes - the keyboard and mouse become totally unresponsive and the only way out is a hard reset (I try using all the keyboard combinations that I've found in my googling  for a solution but they don't seem to do anything - ctrl+alt+backspace,  alt+sysreq+k, alt+sysreq+r-s-e-i-u-b).  There doesn't seem to be any pattern to the freezes, it can be while I'm surfing the internet, playing a game, or just when I come back to the computer after a long period of inactivity it will be frozen instead of on a screensaver.   It happens probably 3-4 times a day, maybe more or less depending on how much I'm using the computer that day (could be frozen all day and I wouldn't know if I'm not using it).  The only thing that could be considered consistent is that I usually have Firefox open somewhere, just because I usually leave my gmail account open.

I've spent several hours googling for troubleshooting tips and haven't found anything that seems to work, so I'm really hoping someone can help me here.  Here's what I've tried so far:

[LIST]
[*]disabling all the BIOS power-related options I can find (I think they are called the 'ATPI' options?)
[*]changing screensaver to just be blank
[*]verifying that the system is not set to go to standby or spin down the disks
[*]disabling putting the display to sleep
[*]typing 'sleep 1; xset s activate' and 'sleep 1; xset dpms force off' like it said to try on this page - [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
[*]possibly a few other things, I've lost track at this point
[/LIST]
Here are my system specs, in case anything may be relevant:

[LIST]
[*]ASRock 770 Extreme3 motherboard
[*]AMD Athlon II X4 620
[*]4GB DDR3 1600G
[*]Radeon HD 4650 video
[*]500GB SATA 3.0 GB/s HDD
[*]SATA dvd burner
[/LIST]
Keep in mind that I'm still pretty much totally Linux-illiterate.  

Any help would be greatly appreciated!

---

### Post by maikel.b on 2010-08-20
Maybe you set the clock of your CPU lower, this has done it for me with a frozen computer.

My AMD 4600 +is now running at 2000 this is   400 mhz lower bud it is stable now! And i got no problems anymore ..

I hope this wil work for you!

---

### Post by Rubi1200 on 2010-08-20
Also take a look here and see if anything fits with what you have been experiencing:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

Good luck!

---

