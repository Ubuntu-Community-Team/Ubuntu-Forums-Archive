---
title: "Missing Disk Space"
date: 2006-03-12
forum: General Help
---

### Post by Aelf on 2006-03-12
I had some sort of error when installing GNUMP3D from packages. This resulted in GNUMP3D filling up the hard drive in /var/log/gnump3d/error.log - 120Gb!

This prevented me from logging in (GDM refused since it couldnt write to some file). Eventually I got into safe mode and deleted some non-essential files, which allowed me to log in.

By using baobab, I found the error.log file and deleted it and then removed it from the wastebasket. 
However, even after a restart, df still shows that my hard drive is 96% full. Baobab reports the same in the summary at the top of the window, however by doing a full scan and manually adding up the totals for each directory, it is nowhere even close to this value. For example, the var directory is a "mere" 18Gb total...
Nautilus reports exactly the same when right clicking on the folders manually and checking the size.

I've tried filling up the space and I get "disk full" errors, even though there should be space there. How can I reclaim this mystery hidden space on my hard drive? I've tried restarting, deleting other stuff (works as normal), but I don't know where to go from here.
Any pointers would be greatly appreciated.

---

### Post by dcstar on 2006-03-12
[QUOTE=Aelf]
......
I've tried filling up the space and I get "disk full" errors, even though there should be space there. How can I reclaim this mystery hidden space on my hard drive? I've tried restarting, deleting other stuff (works as normal), but I don't know where to go from here.
Any pointers would be greatly appreciated.[/QUOTE]
Start a Nautilus session as root, and empty the trash:

gksudo "nautilus --browser %U"

---

### Post by Aelf on 2006-03-12
That fixed it! Cheers for the quick and succint response.

---

