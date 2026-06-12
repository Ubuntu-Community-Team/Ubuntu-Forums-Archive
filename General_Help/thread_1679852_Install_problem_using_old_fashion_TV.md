---
title: "Install problem using old fashion TV"
date: 2011-02-01
forum: General Help
---

### Post by alex341 on 2011-02-01
Couple of years ago, I build a MythTV, based on a Via Epia EX10000EG with a Haupauge PVR500 dual tuner card. Still using a old fashion TV on my TV OUT, I didn't get the best picture, but it worked... 
 
Last year, my HD crashed and only this month I had time to rebuild my MythTV PVR. I downloaded Mythbuntu 10.10, tried to install, but after a while my old fashion TV picture flickered like thefrequency was not correct or the drivers are not suitable for my old tv.
 
After trying with several VGA=771, 770, etc options in the MythTV install configuration, I am out of options. I remember in the 9.04 version there was the possibility to startup in safe screen mode, wich was under F4. This option is now gone. What can I do? What should I add to the boot options?

---

### Post by Kirboosy on 2011-02-01
[LIST=1]
[*]Press *F6* to open the other options menu.
[*]A new window will appear that is totally blank. So now close it.
[*]Command options show up near the bottom of the screen. **Press tab to access these options.**
[*]Press space one (to make some space) and enter the following:     ***–xforcevesa***
[*]Press enter to boot
[/LIST]

---

### Post by alex341 on 2011-02-03
Tnx! Seems to be working...

---

