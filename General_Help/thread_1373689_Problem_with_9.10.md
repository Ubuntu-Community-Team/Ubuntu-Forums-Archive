---
title: "Problem with 9.10"
date: 2010-01-06
forum: General Help
---

### Post by Ronin1of47 on 2010-01-06
I have no prior knowledge of linux but figured it was time to give it a go so i tried installing Ubuntu 9.10, I have been having a problem  after I get it installed it works fine for a few minutes than it freezes, the mouse and keyboard both are unresponsive. I have to manually shut down my machine and reload Ubuntu. i believe it is the update manager that is causing this problem, every time it starts it goes through about 20 or so updates before it freezes, it may also be Firefox as well. I have installed 9.10 3 times (formating the partition before each reinstall) with 3 different disc assuming maybe the problem stemmed from my burned iso file. but same problem all 3 times. I have tried both 32bit and 64 bit. my hardware is, Processor - Intel Core 2 Duo P8600 2.4G, Graphics card - NVIDIA GeForce GT 120M , Memory - 4GB. Any help would be welcomed.

---

### Post by dcstar on 2010-01-06
> **Ronin1of47 said:**
> I have no prior knowledge of linux but figured it was time to give it a go so i tried installing Ubuntu 9.10, I have been having a problem  after I get it installed it works fine for a few minutes than it freezes, the mouse and keyboard both are unresponsive. I have to manually shut down my machine and reload Ubuntu. i believe it is the update manager that is causing this problem, every time it starts it goes through about 20 or so updates before it freezes, it may also be Firefox as well. I have installed 9.10 3 times (formating the partition before each reinstall) with 3 different disc assuming maybe the problem stemmed from my burned iso file. but same problem all 3 times. I have tried both 32bit and 64 bit. my hardware is, Processor - Intel Core 2 Duo P8600 2.4G, Graphics card - NVIDIA GeForce GT 120M , Memory - 4GB. Any help would be welcomed.

Install the **lm-sensors** package and see if your CPU is overheating.

---

### Post by OldGrantonian on 2010-01-06
> **Ronin1of47 said:**
> 
it freezes, the mouse and keyboard both are unresponsive. 


When you say that the mouse is "unresponsive", do you mean that the pointer doesn't move? Or do you mean that the pointer moves, but nothing happens if you click on something?

About once a month, my keyboard and mouse also freeze, although the pointer continues to move. The last time this happened, I noticed that my touchpad was active, so I used it to close down Firefox. After restarting Firefox, everything was OK.

(Of course, that doesn't mean that FF causes the problem. But I'll watch it in future.)

> 
i believe it is the update manager that is causing this problem, every time it starts it goes through about 20 or so updates before it freezes
When I restart, I don't get "20 or so updates". Most times, there are no updates. Because I have dual-boot XP and Karmic, I restart my laptop at least once every 2 days.

Is it possible that you are seeing the same updates every time?

Are you allowed to select only one update at a time? (I'm in XP at the moment, so I can't check). Maybe you can identify the update that causes the freeze.

> 
, it may also be Firefox


See above.

> 
maybe the problem stemmed from my burned iso file
Remember to burn ISOs at the slowest possible speed.

Also, doesn't the Ubuntu CD give you the option to check the CD and memory for errors?

> 
I have tried both 32bit and 64 bit.
I assume your hardware is 64-bit?
.

---

### Post by Ronin1of47 on 2010-01-06
the mouse is completely frozen, touch pad does not respond either (no movement what so ever, caps lock/num lock doesnt even light up the led on my pc) as for the "20 or so updates" all 3 times i did a clean install it prompted me to do updates, a few minutes into the update it froze, and when i restart it freezes again after a few minutes, once the downloads are finished i can open Firefox, but when i try to load a web page Firefox either closes all by itself or my whole system freezes. i could try selecting only one update at a time, haven't tried that. and am re burning iso at minimum speed to try all over again ( uninstalled 9.10 before posting) and i did run disk/mem check and all was fine.

---

### Post by mocoloco on 2010-01-06
Not sure what the issue is but sometimes getting updates will fix all kinds of wacky problems.  Try not even logging in to a graphical session, instead when you get the login screen press Ctrl+Alt+F1 and you'll get a text login (I know you're new, don't worry, it will be easy stuff).  Log in, then type ```
sudo apt-get update && sudo apt-get upgrade
```
You'll be asked for your password again to provide sudo (admin) privileges, then it will show you available updates and ask if you want to install them.  Press Enter for the default [Y] and see if it gets through the updates that way.
When it's done do Ctrl+Alt+F7 to get back to the graphical login screen, and restart the computer.

---

### Post by 3rdalbum on 2010-01-06
Run a memory test from the GRUB menu.

When you use the Update Manager, it loads compressed packages into RAM, and then decompresses them into RAM. In short, it uses a lot of memory, and it's probably reaching a bad spot in your RAM chips.

Run the memory test overnight, and if it gives you any error results then you need to replace at least one of your RAM sticks. Remove one and try the memtest again overnight, and if it succeeds then the one you removed is a dud. If it fails, then put in that stick again and try removing another one. Repeat until you've found the bad one, and get it replaced under warranty.

---

### Post by Ronin1of47 on 2010-01-07
i did the text install of the updates and ran a memory check, memory check came out fine, ran into a problem with updating froze while downloading python 2.6. restarted machine and downloads (via text login) everything was fine for a while ?(about 2 hours) then i turned on "extra" under visual efects, had to download a driver, froze while downloading. restarted machine finished install. everything worked fine for a while (maybe another hour or so)until i opened the software manager while having Firefox open. System froze again... is there any way i can check to see what is causing this? maybe a terminal command or software to tell me what is freezing my system? or does anyone else have any ideas?

---

### Post by OldGrantonian on 2010-01-09
Here's a link on Ubuntu logging (dated about August 2007):

[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-view-logs-with-system-log-viewer.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-view-logs-with-system-log-viewer.html)

I haven't tried it, and I'm in XP at the moment. Maybe someone can comment :)

At the foot of the article, there's a link to boot logging.
.

---

