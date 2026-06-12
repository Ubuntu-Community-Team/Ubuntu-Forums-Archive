---
title: "6870m hybrid graphics?"
date: 2012-09-03
forum: General Help
---

### Post by niai on 2012-09-03
i have been trying for a few weeks now to get my graphics card fully working in pinguyOS (ubuntu 12.04 with few customization). 

if i install the drivers from jockey i get an error instillation failed at the end.

if i install the 12.08 drivers form the AMD site, i can reboot but cant use my card, catalyst say it cant find the card and to do a aitconfig --initialise (-f), if i do this and reboot i get a message saying running in low graphics mode and can only use the terminal(ctarl+alt+F1).

if i install 12.08 and have the integrated turn off at the BIOS or turn it off after, it will work but runs very bad and xorg seems to take up 100% of the CPU after a few hours, i also get problem in windows if integrated is turn off.

i have try a few more things i cant think off atm but still had no luck, so i though i would ask here for any help or a solution?

alienware M17X r3
AMD 6870m
Intel® Core™ i7-2820QM CPU @ 2.30GHz × 8
pinguyOS x64 (with unity)

---

### Post by niai on 2012-09-04
bump?

---

### Post by pqwoerituytrueiwoq on 2012-09-04
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6)
i have had success with this method on a a6-3500 APU

---

### Post by niai on 2012-09-06
tried the link you sent with no luck, i have got it working now with the Intel graphics turn off which works fine now with a BIOS update, this BIOS broke a few things but someone modded them back in.

now that it is working i can say wow AMD graphics really suck in linux, could any one suggest a new NVIDIA card to get for my laptop with grate support?

---

### Post by mastablasta on 2012-09-06
> **niai said:**
> now that it is working i can say wow AMD graphics really suck in linux, could any one suggest a new NVIDIA card to get for my laptop with grate support?
 
 
first you are using a hybrid graphics so look here: [http://ubuntuforums.org/showthread.php?t=1930450/](http://ubuntuforums.org/showthread.php?t=1930450/)
 
second you can't just stick a card into laptop. the one you have now is actually a chip that is on motherboard (the intel one is in CPU). and if you want to easilly switch cards you need a desktop. nvidia hybrids on laptops also don't work in linux (or only some combos work using bumblebee). At least ATI supports hybrid graphics in linux (well on some models..) while nvidia does not support it at all. prompting the F-bomb from Linus.
 
third - ATI graphics suck, but only on certain chips. plenty of them work great.

---

### Post by niai on 2012-09-06
i know the HD3000 is in the cpu and my laptop you can use new cards in it, thay are not solderd to the motherboard (even if it was you can still change its a lot more work lol).

i can turn off the Intel chip making the card standalone thus eliminating the hybrid problem.

from what i read NVIDIA proprietary drives are very good and AMD proprietary suck but open source are very good, the 3D doesn't have go support, and i am wanting to game in Linux. 

and i have followed that link you added far too many times now.

---

