---
title: "transfer drive to new pc build (boot?)"
date: 2011-12-15
forum: General Help
---

### Post by its_jon on 2011-12-15
I am having difficulty booting my ubuntu drive.

I had to get a new mobo/cpu/memory/power supply but am hoping to get my existing ubuntu OS HD to boot inside the new hardware.

The bios does not want to make it easy for me.
I have contacted eclipsecomputers uk who I got the parts from (good guys) and it seems the PC is set up fine.

I think I need to generate a fresh boot sector maybe ???

I have downloaded pupply linux (lucid version) and it has detected the hard drives installed.....

so..... what are the suggestions/options for me to get my ubuntu drive up and running ?....
can I fix it from Puppy ?

thanks

---

### Post by seawolf167 on 2011-12-15
Ensure that the hard drive is recognized in BIOS and that it is flagged as a bootable device with a high enough priority that BIOS attempts to boot it (say #1 is cd/dvd, #2 is your hdd, #3 is usb media).

You shouldn't have to change anything on your hard drive unless this drive originally did not have a MBR on it in your old computer. In this case, you'll need to reinstall Grub2 by following [this guide]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2").

---

### Post by its_jon on 2012-01-23
thanks... fixed now.

I downloaded the boot fixer disk... worked a treat !

---

