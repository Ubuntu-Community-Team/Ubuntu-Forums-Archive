---
title: "Remove all traces of grub"
date: 2011-04-20
forum: General Help
---

### Post by Brudus on 2011-04-20
The other day I repartitioned the drive I had ubuntu on and today I go to start my computer and I get a grub rescue prompt.  I tried the MBR fix on the vista install CD, but that didn't work.  I'm basicly stuck on this liveCD until I can get this fixed.  I would really appreciate any help.

---

### Post by oldfred on 2011-04-21
You should just be able to run the fixMBR command from a windows repair CD.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
BootRec.exe /fixMBR

---

