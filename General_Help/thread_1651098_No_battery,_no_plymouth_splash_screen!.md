---
title: "No battery, no plymouth splash screen!"
date: 2010-12-22
forum: General Help
---

### Post by aala on 2010-12-22
Need help, I installed some stuff and, don't know how but It sure did messed up my laptop.

I installed this wireless [driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") rtl8188c (for my Realtek RTL8188CE Wireless LAN 802.11n PCI-E NIC) and I installed it with success.

I also installed few screen savers from [here]("http://www.n00bsonubuntu.net/content/install-extra-screensavers-on-ubuntu-10-10-maverick-meerkat/"). And again everything went good, but next time I boot the system I noticed that there was no plymouth splash screen playing, and there were just black screen with some text and there was a warning!. It pointed me to a .log file at /var/run/alsa-driver.1188.log, what's inside this file is the following:
```
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -f `find . -name "Module.markers"`
rm -f `find . -name "modules.order"`
rm -rf autom4te.cache
rm -f alsa-kernel/include/version.h
rm -f include/sound
rm: cannot remove `include/sound': Is a directory
make: *** [mrproper] Error 1
```Don't know what the heck is all that about.

Well, and if it was not already enough; it didn't detect my battery anymore after login.
here's a picture. Before any of that happen there were 3 tabs in the "power management" window tool (on ac/on battery/general). Now there's only 2 (the one 4 battery is missing). And if I unplugged my laptop, nothing happens.

Any suggestions???:mad:

All help will be welcome.

---

### Post by aala on 2010-12-22
nobody? :(

---

### Post by aala on 2010-12-23
ahgr Whatever Yo,...

I give up with gnu/linux with this computer, seems like ubuntu or any other major distro can't handle recent hardware properly or at all.

I bought a new computer, because the one I have previously was limiting me a lot due to its age (like 8 years) and "hardware impediments", although I did like it a lot, but I've got to make the transition to new a new PC. But now I can't use this new one with gnu/linux, because it doesn't support anything, no mic, no headphones, no battery, no wifi, no ethernet, no Graphic Card, the webcam looks like crap... %$^&*@#$ man seriously it suxX big time. 

*** Old **LapTop: ***
**HARDWARE**: Compaq Presario Laptop, amd mobile semprom 700MHz, 384MB RAM, 56GB HD. it had an ATI Radeon (forgot the model) with 128MB. 
**SYSTEM**: Dual Boot -- Ubuntu Lucid Lynx/Windows XP

***New LapTop:***
**HARDWARE**: AMD Turion II P540 Dual-Core Processor 2.40GHZ, 4GB RAM, 500GB HD Storage, ATI Mobility Radeon HD 4200.
**SYSTEM**: Previously Dual Boot with Windows 7, not anymore, seems like we ought give it to Win7.
Sytems tested. Ubuntu 10.04/10.10, OpenSuse latest. no luck at all, It's like If gnu/linux community just focuses and targets old cheap hardware. Shame to that. If it keeps on going like that, we are never going to reach up and dethrone MS, and even worse Apple:lolflag:.

Well yeah that was it, I was a full time ubuntu user, now I have to abandon it for the sake of computing comfortableness. Bye Bye Ubuntu see you in like 3 years when you'll have full support for this hardware.

---

