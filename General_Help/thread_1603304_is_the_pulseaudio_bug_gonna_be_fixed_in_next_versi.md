---
title: "is the pulseaudio bug gonna be fixed in next version of ubuntu?"
date: 2010-10-22
forum: General Help
---

### Post by clear on 2010-10-22
was just curious if this bug has been acknowledged by the ubuntu developers and if so, what priority has it been given?

---

### Post by kostkon on 2010-10-22
Bug? What bug? Please, could you elaborate a little more?

---

### Post by The Cog on 2010-10-22
If the bug clear is referring to is the broken sound in my games (no sound in Unreal Tournament, laggy 10 seconds! sound in Doom3), then I'd like to know the answer too.

---

### Post by clear on 2010-10-22
> **kostkon said:**
> Bug? What bug? Please, could you elaborate a little more?

ubuntu 10.10 does not work out of the box with delta 2496 cards. i know the delta 2496 is an old card, but its also a VERY well built and reliable card. the reason why this bug is known is because despite the cards age, many many people still use it. if it aint broke dont fix it so goes the saying. 

and, there IS a bug. one need simply to do a search on the internet for ubuntu 2496 and you will see that a lot of people cant get there cards to work in maverick. something about the cards outputs not being recognized. the user must go through a bunch of ridiculous configurations to get the card working. configurations that most ubuntu users cant get to work because its not easy to figure out to the average ubuntu user. which is joe shmoe from windows. 

the worst thing is i think the developers aren't even  acknowledging the bug because the card is so old. i guess they figure  people can just buy a new card. which is true, but that doesn't really help the situation.

---

### Post by rcrath on 2010-11-15
The bug report with fixes for the ICE1712 chip (MAudio delta series and 2496 and some other brands)  is at [https://bugs.launchpad.net/ubuntu/lucid/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/lucid/+source/pulseaudio/+bug/178442)

It is not too difficult.  There are two options.  First is 
sudo edit /etc/pulse/default.pa 

comment out (Put "#" at beginning of line with no quotes) auto-detection and add the following two lines.  THis is for my card, a Delta 66.  Different cards have different IDs.  Mine is M66.  You can find the ID with 
```
sudo aplay -l
```
here are the two lines to add to the file: 
```
load-module module-alsa-sink sink_name=M66_out device=hw:M66 format=s32le channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
load-module module-alsa-source source_name=M2496_in device=hw:M2496 format=s32le channels=12 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
```

THe other option is slightly more complex and is described in comment 52-53 of the bug report linked to above.

Both worked for me.

---

### Post by rcrath on 2010-11-15
Oh, and then reboot.

---

