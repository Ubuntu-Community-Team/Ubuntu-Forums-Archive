---
title: "cant boot ubuntu on C: because of hall.dll"
date: 2010-12-08
forum: General Help
---

### Post by LinkmanSK on 2010-12-08
Hi i have installed  WINDOWS XP on  E:
Ubuntu on C:

Several weeks ago i can normally choose between xp or ubuntu, now if i choose ubuntu it cant run because that said something like ubuntu cant start because missing hall.dll in windows folder...

i fixed it  in the windows and installed - copied from the win xp pro CD

windows worked normallx
but UBUNTU still cant run 

my boot ini looks like:

[boot loader]
redirect=usebiossettings
redirectbaudrate=
timeout=44
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu\wubildr.mbr="Ubuntu" /fastdetect


Of course that MWR Console does not work , it will restart my pc


how can i fix that problem on the C: if i want to run ubuntu ?

any ideas?

---

