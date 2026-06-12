---
title: "problem in installing ubuntu 9.10"
date: 2009-12-15
forum: General Help
---

### Post by sen2020 on 2009-12-15
hi friends, 
    Im using ubuntu for past 6 month ;) my system works fine :) i recommended my friend to install ubuntu for project purpose..... but its not installing in his computer system... it takes around 20 mins to goto installation... n it struks der i dont know whats the problem :( his motherboard intel 945GCT pentium core 2 duo processor.... do we need any driver software to make it working ????? it works fine with my pentium 4 processor itself..... plz help us friends he need to finish his project by march 2010 :(

---

### Post by audiomick on 2009-12-15
Some things to try.

Have you let the cd check itself? You can do this on your machine if your friend's machine can't read the cd well enough.

I assume you are trying to install from the live cd, so you have it.
Boot from the live cd using the option "try ubuntu without changing the computer" to see if ubuntu runs without a problem on that computer. If it doesn't, there might be a hardware compatibility problem.


If the computer is just having trouble generally with the cd, you might want to try the alternate cd instead. It seems to work better for some people.

---

### Post by sen2020 on 2009-12-15
CD is working fine ;) 3 days back only we downloaded that and installed ubuntu in another friend laptop :) i think some compatibility problem.... how to check it ????

---

### Post by Grey Seal on 2009-12-15
Could be your HD.

GS

---

### Post by sen2020 on 2009-12-17
now we installed 8.04 version of ubuntu :) but my resolution is jus 800*640..... i think i need to install some video drivers....wher can i find it n how to install it ????  n also my sound is very low to hear at full volume.... sound works well with windows xp..... plz   help me soon ;(

---

### Post by sen2020 on 2009-12-17
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)


this is my graphic controller detail when i use tat command

---

### Post by edup_pt on 2009-12-23
Im having problems too. When the cd start i wait... and wait... and then it get me a console window with the user ubuntu. Meanwhile, after a long long time it appears some thing (colors and risks) that i believe to be the start instalation screen. I already tried it in safe mode graphics. 

The computer is new and its a inboard graphic intel vga. The ubuntu is 64bits.

Any suggestions?

Thanks

---

### Post by pianoblack on 2009-12-23
If the installation will not run graphically, then try using the alternate install disk. Provided that this works (Which is likely) then using another computer to download driver fixes, and installing them may help. A scratched disk, or corrupt download is also possible (did you check the MD5 sum?)

---

