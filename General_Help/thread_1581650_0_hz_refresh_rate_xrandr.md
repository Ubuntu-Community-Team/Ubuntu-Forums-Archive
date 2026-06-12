---
title: "0 hz refresh rate xrandr"
date: 2010-09-25
forum: General Help
---

### Post by BokiZoki on 2010-09-25
Hey! I am experiencing some problems with xrandr. I have just installed  Ubuntu Netbook remix 10.4 on my asus eee pc 1001ha and the default  1024x768 resolution has rafresh rate of 0hz.
So i searched the net  and found xrandr. I used cvt and xrandr --newmode <modeline> to  create mode , added it to output, but when i try to change mode like  this: xrandr --output default --mode prava, the xrander does nothing and  the reslution stays 1024x768 0hz. I can see new mode: 

netbook@netbook-laptop:~$ xrandr
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  
   800x600_75.00   74.9  
   prava          74.9  

but can't switch to it. The star indicates that default resolution and refresh rate is active.

Maybe I could try with xorg.conf but i do not know what lines to put in it since i am new linux user.


I would really appreciate your help.
Thanks

---

### Post by doru001 on 2011-05-26
I fully recommend this page: [* Modeline Calculator]("http://www.arachnoid.com/modelines/index.html")

---

