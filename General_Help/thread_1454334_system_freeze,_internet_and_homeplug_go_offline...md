---
title: "system freeze, internet and homeplug go offline.."
date: 2010-04-14
forum: General Help
---

### Post by noveevon on 2010-04-14
hi, 

i made a thread about how WMware made my homeplug internet system go offline earlier see here: 

[http://ubuntuforums.org/showthread.php?t=1452848](http://ubuntuforums.org/showthread.php?t=1452848)

>  				 				**WMware, kubuntu, Devolo homeplug problem.** 			
 			 			 		   		 		 		Hi,

i am experiencing problem with my home-plug arrangement due to my WMware  internet connection..

ive had a similar problem using virtualbox and that is why i switched to  WMware..the problem is as follows, when i start to download something  via the net in my WMware machine, my home-plug looses its connection to  the net..ive tried both NAT and brigde without any difference... 

i have used WMware for a while without this problem, but since ive  experienced a similar problem with Virtualbox i am pretty sure its due  to the software and not my home-plug..


anyone else been experiencing problems with their internet as a result  of using a virtual machine?



now it seems that it is probably not due to WMware as now it is happening at a very rapid pace, i only have a few minutes on my computer before the system freezes up and i cannot open or close windows etc...

i can move my mouse though...


its not due to my hardware as its upto date, but it might be due to my ATI drivers and Xorg? but i dont know how to verify this suspicion?


i am using 9.10 kubuntu...

also, might updating to 10.4 solve my issues? i do need to be able to use the standard ATI drivers, as they control my maniac graphics card fan, as it is really noisy and i cannot use it on default speed...

so do the 10.4 now support ATI standard drivers? if so i could just update?

---

### Post by noveevon on 2010-04-14
i think its Xorg as i tried > sudo dpkg-reconfigure xserver-xorg and now my system is pretty stable...no internet problems since...

---

