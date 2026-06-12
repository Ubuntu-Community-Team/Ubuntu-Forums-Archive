---
title: "ATI Clock Settings"
date: 2012-08-26
forum: General Help
---

### Post by alevkov on 2012-08-26
Hi, i have an XFX 4870 1GB ATI Card and huge problems in linux to  control the clock settings. Usually i use CCC in Windows to control the  temperature and the fan workrate of the card, this is easy done in CCC's  Overdrive Tab, where i just need to accept the agreement and then  scroll the gpu and mem clocks lower (to 600, 450 minimum). This is makes  an huge difference into the temps, like 10 C at iddle. Without running  CCC on Windows the temp is X+10 C at iddle, then i run Catalyst Control  Center where i have Overdrive active and temps colds back to X C.  

So, this is my problem, i really want too run linux but not without  this control. ATI Drivers on Linux are shite and do not change the  clocks over -aticonfig --odsc etc,,, (yes i have tried the official  driver, and yes i have reinstalled everything more than once).  

My question is, is there a way to set the GPU clock settings to  minimum in the BIOS? Or is there any other way to set it so that Linux  doesnt have to deal it (the logical result of this would be that i don't  need Catalyst in Windows?!?!)  

Thanx in advance, deshardi   

ps. sorry if it s the wrong subforum, if so please mods move it.

---

### Post by Rexilion on 2012-08-26
Maybe [this]("https://bitcointalk.org/index.php?topic=25750.0") could help?

---

### Post by alevkov on 2012-08-26
> **Rexilion said:**
> Maybe [this]("https://bitcointalk.org/index.php?topic=25750.0") could help?

I took a read there, the most interessing answers are : 

"If --od-enable could make it, this will do it too." 

Which in my case wasn't able to do so....

Anyway thanks

---

### Post by alevkov on 2012-08-27
I m sorry for double posting but since i resolved the problem nd found an major solution i guess it s worth it. 

The Issue was sorted with the RBE tool under DOS. Flashing BIOS made my card accept the new clock settings and i am now just bout to install Ubuntu in seconds, without any need to have "control" of it under the same OS. 

This can also be done for overlocking, just Google RBE tool nd ya gonna find a full tutorial how to use all methods.

---

