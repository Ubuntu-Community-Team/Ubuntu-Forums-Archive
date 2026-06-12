---
title: "bluetooth gpsd / rfcomm/ 3rd party app issue?"
date: 2010-07-06
forum: General Help
---

### Post by ubermunkey on 2010-07-06
Hi!
This is my first post here. I will try and post everything I have done up to this point to resolve my issue.

System Details:
       Hardware Environment:
[INDENT]Gateway NV5927u ( with i5 not i3 proc) .
[/INDENT][INDENT]4Gb ram / BlueRay drive / as per i5 reqs..integrated video / 
[/INDENT][INDENT]external USB bluetooth ( see : [http://www.iogear.com/product/GBU421/](http://www.iogear.com/product/GBU421/) )
[/INDENT][INDENT]bluetooth GPS Receiver ( see : [http://www.usglobalsat.com/p-630-81-bt-359w-main-unit-only.aspx](http://www.usglobalsat.com/p-630-81-bt-359w-main-unit-only.aspx) )
[/INDENT]       Software Environment:
[INDENT]Ubuntu 10.04 via upgrade from 10.04 beta release ( i.e: not fresh from LTS dvd )
gpsd version: ```
:~$ gpsd -V
gpsd: 2.92 (revision svn)
```
blueman version 1.21
xgps version: while unable to get version from xgps -V , it is the current version from the ubuntu repo installed with gpsd-clients
[/INDENT]Things I have tried so far:
[INDENT]Followed tutorials found here at [http://ubuntuforums.org/showthread.php?t=200142&highlight=bluetooth+gps](http://ubuntuforums.org/showthread.php?t=200142&highlight=bluetooth+gps) and [http://www.gp32x.com/board/index.php?/topic/54520-bluetooth-gps-and-tangogps/](http://www.gp32x.com/board/index.php?/topic/54520-bluetooth-gps-and-tangogps/)
None of which worked.

[/INDENT]Some output from what appears to be a valid connection:
[INDENT]I have run sdptool browse and found my device
I have used hcitool scan and found my device
I have done a cat of /dev/rfcomm0 and seen data streaming
I have seen a process id for gpsd as well as seen a listneing port for gpsd 
I have been unable to get either gpsdrive / xgps / tangogps to see gpsd. All report it as not running.

[/INDENT]I have used ever resource I KNOW to use to fix this issue. Could use some help.

---

### Post by ubermunkey on 2010-07-06
am i the only person having this issue?

---

### Post by zzart on 2010-07-09
> **ubermunkey said:**
> am i the only person having this issue?

yep me too. apparently there is a bug in 10.04 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/570692](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/570692)
 or 
my feeling is that gpsd is no longer reading rfcomm4 ( or whatever) port. 
i will try to research the gpsd. since both of us have an output via
cat /dev/rfcomm4 then there is no problem with bluetooth itself , rather it would suggest the program / deamon phrasing output....  
sorry can't help here

---

### Post by ubermunkey on 2010-07-09
yeah. Thanks for the bug link! upon looking around I have seen a few issues related to the blueZ; as well as, gpsd and its new API ( not that i understand that ). Thanks for checking in.

---

