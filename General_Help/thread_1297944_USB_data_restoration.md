---
title: "USB data restoration"
date: 2009-10-22
forum: General Help
---

### Post by ZymbiotiZ on 2009-10-22
heya,
anyone worked anything with restoring data from a USB flashdrive that's somewhat crashed? =/
 
It's a .pst I need to get hold on from my 16gb USB-thingy (SanDisk Cruzer with U3-utility)... whenever I plug it in running WinXP everything gets a pretty big delay and when clicking the disk (when it finally appears in explorer) it says after a while "this disk is not available due to a i/O-error"
 
I tried reaching it in ubuntu as well, I found the disk, and actually the folder where the pst is stored, but couldn't access it. I did however find another file that's on the disk (Kung Pow, enter the fist (wich is an awesome movie btw ^^)), and this could be moved or copied freely, but when I tried copying the other folder with the oh so important .pst i only get "input/output error"...
 
It also have a tendency to stop OS' from booting or shutting down... windows can't shut down at all if the USB is still plugged in, ubuntu had no problem, but was running on a live cd, since I'm still stuck at work and ain't got my own laptop with me...
 
anyone got any ideas? :S

---

### Post by Giblet5 on 2009-10-22
> **ZymbiotiZ said:**
> heya,
anyone worked anything with restoring data from a USB flashdrive that's somewhat crashed? =/
 
It's a .pst I need to get hold on from my 16gb USB-thingy (SanDisk Cruzer with U3-utility)... whenever I plug it in running WinXP everything gets a pretty big delay and when clicking the disk (when it finally appears in explorer) it says after a while "this disk is not available due to a i/O-error"
 
I tried reaching it in ubuntu as well, I found the disk, and actually the folder where the pst is stored, but couldn't access it. I did however find another file that's on the disk (Kung Pow, enter the fist (wich is an awesome movie btw ^^)), and this could be moved or copied freely, but when I tried copying the other folder with the oh so important .pst i only get "input/output error"...
 
It also have a tendency to stop OS' from booting or shutting down... windows can't shut down at all if the USB is still plugged in, ubuntu had no problem, but was running on a live cd, since I'm still stuck at work and ain't got my own laptop with me...
 
anyone got any ideas? :S



You need to accept the fact that the data is most-likely beyond recovery.

If it's critical, then pony-up the $3000-$10000 for a professional recovery service.

If it isn't critical, try to fix the stick's filesystem.

Boot Windows. Bring up Windows Explorer. Right-click the stick. Select Properties. Click the Tools tab. Click the "Check" button. Enable automatic fixing.

When (if) it completes, right-click the stick again and select "Eject". It will disappear from Explorer. Pull it out, wait 5, plug it back in.

What was easily recoverable is right there...

---

### Post by ZymbiotiZ on 2009-10-24
thanks for your input mate, I tried what you said but I couldn't even bring the menu up to select properties, the USB is that ******.. .^^
 
However I did find a program called BadCopy Pro ( [http://www.jufsoft.com/badcopy/](http://www.jufsoft.com/badcopy/) ) that managed to do the trick! :D 
Alond with a few hundred other long gone deleted files, the .pst was finally retrieved again.. =)

---

