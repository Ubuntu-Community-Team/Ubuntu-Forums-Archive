---
title: "Ubuntu is *painfully* slow"
date: 2010-03-08
forum: General Help
---

### Post by kaldor on 2010-03-08
I have a Dell Optiplex computer. On all computers I have used it on, even those with very low specs, Ubuntu has run fine. But on this Dell... Ubuntu is worse than Windows Vista running on 512 MB.

It came with XP. I reformatted it and used Fedora. Everything was zippy and fast. But then I decided to install Ubuntu... and I am amazed at the performance drop. 

512 MB RAM and 3 Ghz processor. Not too bad. But Ubuntu is actually painful to use. I shouldn't have to wait 10 seconds for the Applications menu to pop up. I shouldn't have to wait up to a minute to load up a program as simple as Gedit. Browsing the net on Firefox is dreadfully slow. Web pages take forever to load. Even the right-click menu on the desktop takes a while to load! The computer is quiet, but as soon as I click something, move the mouse it's loud.

Any ideas what this could be? It's a vanilla installation. The only thing I did was change the wallpaper and disable desktop effects. Because that's all I can do.

Edit: I'd like to add that I had to use another computer to post this because Ubuntu couldn't load up the forums. It's really this bad. 

Edit2: The screen is now totally locked up. I can only move the round "loading" cursor around. Clicking on things do nothing. 

This is the same disc that was usedto install Ubuntu on 3 other computers, so I'll rule that out. Reboots/shutdowns do not help the problem either.

Sorry if it sounds like I am complaining too much, I'm just trying to provide as much info on the issue as I can :)

---

### Post by Slim Odds on 2010-03-08
It is most likely a problem with the computer, not the OS.

---

### Post by kaldor on 2010-03-08
> **Slim Odds said:**
> It is most likely a problem with the computer, not the OS.

Then why did it run faster on Windows and Fedora? These problems happened ever since I installed Ubuntu. The LiveCD ran quite a lot faster than it is now.

Edit: I booted up Karmic's LiveCD on that computer. The CD is many times faster than the actual installation. Think a reinstall may help? I booted back into Ubuntu. Everything's fast and normal again, even on the "Extra" visual settings. Strange that it was so slow.. I rebooted a few times before and it did nothing. I'll post again if this happens more.

---

### Post by robert shearer on 2010-03-08
> **kaldor said:**
> Then why did it run faster on Windows and Fedora? These problems happened ever since I installed Ubuntu. The LiveCD ran quite a lot faster than it is now.

Edit: I booted up Karmic's LiveCD on that computer. The CD is many times faster than the actual installation. Think a reinstall may help? I booted back into Ubuntu. Everything's fast and normal again, even on the "Extra" visual settings. Strange that it was so slow.. I rebooted a few times before and it did nothing. I'll post again if this happens more.

Applications=>Accessories=>Terminal and type:

```
top
```

Minimise this window and then next time the compy slows up maximise it and see what process is using the cpu.

Report that info and we will have something to follow up, rather than 'it is slow'. ;) :)

---

### Post by Slim Odds on 2010-03-09
Even better, install htop and use that

Just one more note that I've mentioned many times before.....

Millions of people run it without issue. Therefore, if there is a problem, it's something unique to the hardware combination that you are using.

---

