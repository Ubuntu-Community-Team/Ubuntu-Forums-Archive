---
title: "tasksel install removed a bunch of stuff - how to get list?"
date: 2012-08-05
forum: General Help
---

### Post by fitzhugh on 2012-08-05
I tried running tasksel for the first time on this computer - xubuntu 11.10. It seemed to be taking a long time to launch. I switched focus from the terminal window to another application, then returned a while later. 
Instead of showing the list of things to install that I expected, it was showing the progress bar and below showed the changing list of things it was installing and removing: kde stuff was being added, I saw vlc removed, then tried killing it. Had to actually close terminal, which didn't stop it, so I went to another and did a killall on aptitude. 

What have I done? Anything I can do to get a list of changes made? I don't want to reinstall everything, but I really don't want to keep finding missing apps. Of course I don't have a backup. 

I just launched tasksel again, and the only things checked were "basic ubuntu server" and "print server" 
cat /etc/issue shows Ubuntu 11.10
Should it show xubuntu? I don't recall.

Any advice would be great - thanks!

---

### Post by fitzhugh on 2012-08-06
OK - still NO idea why this happened. When I tried to close tasksel again it actually switched to showing aptitude running again. Just freaky. Obviously I'm overlooking something, just no idea what.

However, I found the list of what had been done. It was obvious when I actually thought about it: the changes showed up in /var/log/apt/

---

### Post by supermango on 2012-11-28
> **fitzhugh said:**
> OK - still NO idea why this happened. When I tried to close tasksel again it actually switched to showing aptitude running again. Just freaky. Obviously I'm overlooking something, just no idea what.

However, I found the list of what had been done. It was obvious when I actually thought about it: the changes showed up in /var/log/apt/

Great! I did the same thing. I was trying to install Lamp Server and without thinking too much about it, deselected the things that I didn't need (as I already had them installed). And when I clicked OK, *boom* there goes my ubuntu installation. I lost everything. I not only have to reinstall, but also customize and set my preferences again.

There needs to be better warnings in TASKSEL for n00bs like us.

---

