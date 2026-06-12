---
title: "Removal of trojans before getting rid of windows."
date: 2011-07-20
forum: General Help
---

### Post by Leovinus on 2011-07-20
Hi all.  I have a machine duel booting Ubuntu 10.04 and XP, after a recent trojan infection on the dreaded windows side on my system I've decided to simply delete all bar the file storage on the windows partition and rid myself of windows for good.  Since my machine is networked with windows computers I want to make sure that there are no windows viruses on it as I don't want to ruin anybody else's system.  I have tried scanning the windows partition from Ubuntu but have not been able to detect any viruses I was wondering, does anybody know where trojan's tend to place themselves?  Do trojan's generally spread themselves to file storage areas or do they usually confine themselves to active areas like the registry?  In other words, if I delete all of the functional windows areas leaving only the contents of my documents how certain can I be that I have removed all of the trojan's?

Sorry this is a bit of a windows question but I intend for it to be the last because I can't wait to see the back of it!  Any information on this subject would be greatly appreciated.

Thanks.

---

### Post by dasan on 2011-07-20
When i was using windows before what i used to do to find out infection is to check installation drive,windows path and system and system32 for hidden system exe files 
you can do it by taking a terminal and typing
dir /ash

which will list all system hidden files..

windows never keep any exe files as system hidden (As per my knowledge till XP)

and you can delete any of such files

---

### Post by grubbymitts on 2011-07-20
Well, thinking logically, a trojan delivers viruses to the operating system.  The viruses need an operating system to run, so if you delete the OS element and just keep the documents then any virus that you've missed would be a non-working executable and harmless.  
 
Of course, you could manually place the viruses on another windows machine and get them to execute that way but they wouldn't go there themselves.

---

### Post by coffeecat on 2011-07-20
> **Leovinus said:**
> I've decided to simply delete all bar the file storage on the windows partition and rid myself of windows for good.

If you leave some stored files behind, you need to be aware of the potential for downloaded jpegs, mp3's and other types of file to masquerade as or contain malware. "Free" Windows screensavers are another possible source of malware. They won't affect Ubuntu, but if you are sharing on a network there is the possibility that infected files, if present, could affect Windows machines.

---

### Post by dasan on 2011-07-20
Update:
In case of any infected file ... my above solution will not work 

As a permanent solution you should throw windows in garbage :D

---

### Post by Leovinus on 2011-07-21
Thanks everybody, that's some helpful information.  I'll certainly be getting rid of windows as a boot option now, from now on if I need to run any windows programs it will be with Wine or windows running in Virtualbox where it can be kept under tight control!

All the best.

---

### Post by haqking on 2011-07-21
just keep your files in a seperate partition or back them up to an external hdd or whatever.

Get rid of windows.

use clamtk in ubuntu to scan that partition or externall HDD.

then forget about viruses for the most part.

done

---

