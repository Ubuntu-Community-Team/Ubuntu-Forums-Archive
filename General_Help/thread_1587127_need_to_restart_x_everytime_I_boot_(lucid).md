---
title: "need to restart x everytime I boot (lucid)"
date: 2010-10-03
forum: General Help
---

### Post by koopke on 2010-10-03
Hi

Im using ATI mobility radeon HD 5870 on Lucid (10.04) 64 Bit
kernel 2.6.32-24

 installed the fglrx driver (catalyst 10-9) and everytime I reboot I get this msg

"
Ubuntu is runing in low-graphics mode

the following eror was encounterd. you may need to update your configuration to solve this.

(EE) fglrx(0): ACPI:DRM connection faild 
(EE) fglrx(0): ACPI:DRM connection faild 
(EE) fglrx(0): atiddxDriScreenlnit faild, GPS not been initialized
(EE) fglrx(0): xmm faild to open CMMQS connection
(EE) fglrx(0): xmm faild to initialize
(EE) fglrx(0): firegl-setsuspendResumeState faild-9

"

and then i need to restart x in order to get into the desktop

after uninstall the fglrx its disapear but after reinstall it the problem comes back.

any ideas how to solve this and make fglrx work on my system?

thanks

---

### Post by P4man on 2010-10-03
I read somewhere hat running

```
sudo aticonfig --initial
```

fixes it. Worth trying I guess.

---

### Post by koopke on 2010-10-05
Unfortunately it didnt solve the problem.

any other ideas someone? 

do you thinks that if I upgrade to ubuntu 10.10 (maverick) it might solve the problem?

---

### Post by P4man on 2010-10-05
Definitely not. I cant even get ATI drivers installed on 10.10 (works fine on 10.04 for my card).

Anyway, maybe you could try grabbing drivers from ATI's website?

---

### Post by koopke on 2010-10-05
so in that case... 

can I "downdate" my ubuntu to an older one 
or should I need to uninstall the Lucid and then install the older ubuntu?

---

### Post by P4man on 2010-10-05
10.10 = maverick, its still in beta. Im just telling you its a bad idea to try and fix ATI problems by upgrading to 10.10 as ATI drivers have plenty of problems with 10.10.  I cant even get them installed with my ATI 4870, whereas they are least work somewhat on 10.04.

How I miss my nVidia card :(

10.04 = lucid, is the current version and usually works okay(ish with ATI). 

That said, googling I see plenty of users complaining about ATI drivers on the 5870, I dont see any that are really solved. 

If you dont need bleeding edge 3D performance in ubuntu, you could perhaps stick with the opensource drivers installed by default? Not sure if they support your card, but I think so. One problem is that they dont support powermanagement features yet, so they will kill your battery (assuming a laptop).

Or try the latest drivers from ATI website. Follow their elaborate instructions to install them.

Maybe someone else has a better idea though.

(btw, you can not downgrade ubuntu).

---

### Post by koopke on 2010-10-06
thank you very much. 

my "use to work fglrx driver" was actually from the ATI website


So, for now I installed the open source drivers and like you saied everything is working just fine, 
eccept I cant use compiz threfore I cant use the [COLOR=black]magnifying glass (for the desktop) wich was use to be really helpfull for me. and as you saied the power mannagment is really "bad"

guss  that I will remove ubuntu and install an older version cuz the magnifier was really important for me. 

10x again for you help. 


[COLOR=#000099][/COLOR][/COLOR]

---

