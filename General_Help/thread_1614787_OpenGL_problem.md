---
title: "OpenGL problem"
date: 2010-11-06
forum: General Help
---

### Post by thewraith420 on 2010-11-06
Hi guys, I'v been a windows vista user for a while now but decided to give ubuntu a shot on the advice of a friend. I am running Ubuntu 10.10 and for the most part things are running smoothly but something i havent been able to work out yet is getting the open source drivers to display openGL games and apps properly. I'v checked for proprietary drivers only to find that they don't support my integrated card anymore. It's an ATI Xpress 200G series card. Is there anything i should try in order to resolve this?? If a different distro of linux could be more compatible with my hardware i'd be open to changing distro's as well.

Thanks,

---

### Post by lykeion on 2010-11-06
I can't find any ATI Xpress 200G card (only 200, 200M, 200P). Are you using a desktop PC or a laptop?
Can you start a Terminal (Applications > Accessories > Terminal), and paste the output of this command (and wrap it in CODE tags like I've done here):```
lspci | grep VGA
```

---

### Post by thewraith420 on 2010-11-07
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
```

It's an integrated card in a compaq presario sr1810nx desktop.

---

### Post by lykeion on 2010-11-07
Your description of your problem is very vague. Could you explain exactly what problems you encounter.

According to this page the open source driver for the rs480 chipset should support 3D acceleration (OpenGL). 
To check this enter this command in a terminal (it should output Yes if supported):```
glxinfo | grep 'direct rendering'
```
To check performance you can run glxgears (let it run a while and notice fps):```
glxgears
```Read about the open source driver here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
You can also test the proprietary driver, see here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

