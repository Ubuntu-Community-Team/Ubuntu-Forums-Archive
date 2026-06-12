---
title: "Noob with hot laptop :/"
date: 2011-09-14
forum: General Help
---

### Post by Solaar on 2011-09-14
Yo :)

Started using Ubuntu 10.04 LTS about a week ago and its awesome!! 

Problem  is my laptop (Acer aspire 5810tzg) gets seriously hot while running  ubuntu, even if I'm not running any programs (hotter than win7 did when  it was rly busy).  Doesnt overheat and shut down tho, but im pretty  confident i could cook a meal under there :P and I'm too noob to figure  out the computertemp addon to be more specific about the tempratures:sad:

Some specs:

1.3GHz Intel Pentium Dual-Core SU4100 (cpu1: 8-12% cpu2: 8-10% average use in standby )
 800MHz FSB
 ATI Radeon HD 4330 512mb
 500GB 5400rpm SATA HDD (everything is on one disk, no partions etc)
 4GB (2x2GB) DDR3 RAM

OS: Ubuntu 10.04 lucid - gnome 2.30.2 (32-bit)
Came with win7 HE 64-bit (if thats relevant?)

Anyone  know what causes this? and if there is any way i can fix it? If not, is  there any lighter distro i can try? I need a stable distro to run Gimp,  Bluefish, a good browser , play music and videos and be able to  download stuff:wink:  would be nice (but no must) with an ubuntu/mint feel to it aswell if  there is a distro like it? I'm a complete Linux noob so plx go easy on  the reply if its a repair issue^ ^ [-o<

---

### Post by mycroft on 2011-09-15
First off, try following this guide [https://help.ubuntu.com/community/SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto") to install sensor software (assuming it isn't installed already) and see how hot the laptop actually becomes. At idle operation (doing nothing) it shouldn't normally go beyond approx. 60 degrees Celsius.

Depending on the age of the computer it might be that it is in need of an internal cleaning. Over time, dust and various particles may accumulate inside or in front of the fan, seriously impeding the airflow needed to dissipate heat from components such as processor and graphics chip. 
If this is indeed the issue, you might be able to solve it using blasts of compressed air aimed at the air intake/exhaust grill. You would have to insert a long, thin piece of plastic to prevent the fan from spinning when hit by the blasts of compressed air. Otherwise, the fan may be damaged.

Opening the laptop case and exposing the fan [and/or the heatsink depending on design] allows you to be more thorough, and possibly apply new cooling paste as well - but don't go there if you're uncomfortable doing this or unable to have someone more experienced assisting you.

---

### Post by 3rdalbum on 2011-09-15
You have an ATI Radeon HD graphics chip - have you installed the ATI driver from the Additional Drivers program? If not, you should; it probably has better power management and can run your graphics chip cooler than the default open-source driver.

---

### Post by Solaar on 2011-09-15
First I wanna say thanx alot for the replies :)

All tempratures showed is between 82-94 degrees celcius, this is with the laptop standing flat out at a cold stone table doing nothing.

Tried  installing the ATI driver, but after I installed it and reboot for it  to work my screen is all black after the Acer(hit f2 for setup) screen.  Is there any way i can reverse it? To take backup n such before evt.  installing a new distro/fixing the issue (not very important atm but  would nice) Do u think the same will happen if I install Mint 11 and  then get the ATI driver?
Booted Mint 11 kataya from a flashdrive now and repeated the the process and now it is 

mint@mint ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +72.0°C  (crit = +98.0°C)                  
temp2:       +72.0°C  (crit = +98.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +78.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +74.0°C  (high = +105.0°C, crit = +105.0°C)  

Its  alot better so guess Mint finds my hardware more tasty? Or did the temp  drop because I havent installed it yet? What do you guys think?
Will try the air trick tomorrow when i have access to the compressor to see if what difference that makes.

---

