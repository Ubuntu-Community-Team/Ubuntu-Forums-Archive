---
title: "I just cant remove ubuntu from boot"
date: 2009-08-03
forum: General Help
---

### Post by freeddy85 on 2009-08-03
Hi tried intall ubuntu from windows xp,, but it diden go well becuae i coulden get it to work with my raid 0.. but i get ubuntu in boot menu.. and i could NOT find it in boot ini file..

So now i installed windows 7 only because i hoped it would remove ubuntu from boot,, but noooo..

i have tried Bootrec.exe /FixMbr =not solving it

this is what bcdedit shows:

Microsoft Windows [Version 6.1.7600]
Copyright © 2009 Microsoft Corporation. All rights reserved.

C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier {bootmgr}
device partition=\Device\HarddiskVolume1
description Windows Boot Manager
locale en-US
inherit {globalsettings}
default {current}
resumeobject {f5526cea-c4e7-11dc-9c48-0018f300e662}
displayorder {current}
toolsdisplayorder {memdiag}
timeout 30

Windows Boot Loader
-------------------
identifier {current}
device partition=C:
path \Windows\system32\winload.exe
description Windows 7
locale en-US
inherit {bootloadersettings}
recoverysequence {f5526cec-c4e7-11dc-9c48-0018f300e662}
recoveryenabled Yes
osdevice partition=C:
systemroot \Windows
resumeobject {f5526cea-c4e7-11dc-9c48-0018f300e662}
nx OptIn

C:\Windows\system32> 

i realy want to remove it,, pls help

---

### Post by Primefalcon on 2009-08-03
If you dont want ubuntu and want to reinstall windows anyhow, all you do is boot windows from disc, delete all partitions, create new big partition and install windows that it..... nothing fancy, you only need to fixmbr if you are still wanting to keep the installed windows and make that primary

---

### Post by freeddy85 on 2009-08-03
Hi Primefalcon,

as you could see i have just installed windows from scratch,, and i have so many hd drive and would like not to format all off them.. and im not sure if it would have solved the boot issue

when i tried intall ubuntu i notice it did make an folder called ubuntu (i did use the option called install in windows) and i that folder did i manage to delete

---

### Post by Primefalcon on 2009-08-03
you only have to worry about the boot drive not a slave drives

---

### Post by freeddy85 on 2009-08-03
How do i remove it from boot?
when i start my computer i get windows boot manager and both windows 7 and ubunutu is precent..

I dont have ubuntu on my computer and want to reomve it

---

### Post by wojox on 2009-08-03
A.) Boot off your Windows XP CD.

   1. Choose “Repair”
   2. When it asks for the installation number, put in “1&#8243;, and it worked fine (you may want to test this first to be sure.)
   3. Enter Admin password.
   4. At the command prompt type “fixmbr”, then confirm. Windows will overwrite the dual boot info in the MBR that Ubuntu put there.
   5. Reboot!

---

### Post by freeddy85 on 2009-08-03
> **wojox said:**
> A.) Boot off your Windows XP CD.

   1. Choose &#8220;Repair&#8221;
   2. When it asks for the installation number, put in &#8220;1&#8243;, and it worked fine (you may want to test this first to be sure.)
   3. Enter Admin password.
   4. At the command prompt type &#8220;fixmbr&#8221;, then confirm. Windows will overwrite the dual boot info in the MBR that Ubuntu put there.
   5. Reboot!

I have tried that for a long time ago.. but that ubuntu is stuck at my startup and that fix did not solve it.. and if you read what i have done you could se i have installed windows 7

---

### Post by Primefalcon on 2009-08-04
> **freeddy85 said:**
> I have tried that for a long time ago.. but that ubuntu is stuck at my startup and that fix did not solve it.. and if you read what i have done you could se i have installed windows 7
Within the windows 7 setup just go custom options and selecting the partitions and pressing the delete key (yes that simple) and then create one that uses all your hard drive and then format and install to that and everything bar the fresh windows 7 is gone from it......

---

