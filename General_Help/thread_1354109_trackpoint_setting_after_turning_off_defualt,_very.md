---
title: "trackpoint setting after turning off defualt, very slow"
date: 2009-12-13
forum: General Help
---

### Post by mikecarlone on 2009-12-13
hi everyone, the trackpoint was working with ervery version of ubuntu. i never had a problem, because i was doing what to need in order to work it. and now i think after i installed gpointing setting device had problem. now after turning off the laptop the settings in configure trackpoint are default. also the sensitivity and the speed of trackpoint are very slow.
rc.local, sysfs.cnfg also added to startup, but no success yet.

how can i solve this problem

thx.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8485025") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8485025")

---

### Post by mikecarlone on 2009-12-13
ok. boys, no one help me. i think there is no body who know with trackpoint or something like that
thx.

---

### Post by mikecarlone on 2009-12-13
i also added the settings

echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed
echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select


to rc.local but no success yet.i dont know why. for 3 years i have been using it and suddenly it doesnt work .

i realy dont know why its so. i did every thing but it always fails. if i restart the laptop it work. or if i turn off the laptop and turn on in 2,or 3 seconds again it works. but if i turn it off  and wait 10 seconds or more it doesnt work anymore???

any help for me ??? in other case i muss  reinstall ubuntu.9.10

---

### Post by mikecarlone on 2009-12-13
i reliased the problem is rc.local doesnt work at start up. now the question is how can i start it at boot up?

---

