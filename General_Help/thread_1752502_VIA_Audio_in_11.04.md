---
title: "VIA Audio in 11.04"
date: 2011-05-07
forum: General Help
---

### Post by Grisk13 on 2011-05-07
Hello, everyone!  Relative newby here (Been playing with Linux since 9.10, only going full linux this summer) and I am having an issue I can't find much information on.  I was able to fix an issue I was having with my wireless drivers by compiling a new set of drivers from the manufacturer (and fixing kWallet :P), and I am hoping this has a similar solution, but I am genuinely confused!  

I have an Asus P7P55D-E Pro motherboard with an integrated VIA VT1828S Audio chip.  It works  a treat with my amps (Digitech RP255 into a Fender Squire and a Line6 Spider3-15) but it does not recognize my headphones at all.  alsa-mixer will show a headphones slot, but adjusting the volume does nothing.  In Unity, if I switch the default sound device to Analog Headphones, I get zero sound, and under KDE (My usual desktop)I have nothing but speaker sound.  

Some searching around turned up some issues with speakers failing, but nothing about headphones coming up

---

### Post by Grisk13 on 2011-07-26
I have actually been working on Linux again after a break.  I am still having this issue, and my searching has led me back to my own post!  

Does anyone have any insight into the issue?  At this point, I would just appreciate supplemental reading :confused:

Just because I learned something:  By switching "Independent" in Alsamixer (playback tab) to Off, I am able to get sound out of my headphones, but sound in the speakers does not turn off when the headphones are plugged in.  I hope that helps!

---

