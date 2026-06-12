---
title: "Mouse Issue on Ubuntu"
date: 2010-05-06
forum: General Help
---

### Post by Khary on 2010-05-06
My problem is very strange one.
Intel Pentium III Processor
535.4 mhz
720 - 896 ram (depending on how many things i put in)
 
This system would seem slow for Linux, but it really is just fine for my purposes.
Anyways...
 
I had microsoft xp installed on my main harddrive. I proceeded to install Ubuntu 9.10 to try it out (only cd i have, will install to latest Ubuntu v.10). Well, i liked it. So, since i didn't have enough space on my main harddrive, i just installed it again, deleting Windows Xp in the process (i copied all the needed data on an external hard drive beforehand). I tried gparted before, but i thought that just installing Ubuntu again would be faster.
 
One key thing i should note is that i've recently added some ram and changed around the placing of it. After doing this, i've had the problem of the computer making a funny whirring noise (very distinct), and after about 30 seconds after this noise, the mouse would stop moving and the whole computer would freeze, forcing me to reboot or shut off. I ran memtest, and it turned out that there was some bad ram, so i replaced it for a total of 720 ram (896 before i did this, 720 is what was there originally without any problems). I did memtest on the whole ram. I then proceeded to test each and every ram chip to see what the problem was but there were no errors detected (i ran just 1 pass though). Anyways, after trying to figure out what the ram problem was, i just quit.
 
So, i then installed Ubuntu 9.10, without any problems. Following upon my previous intention, i then proceeded to install the latest version of Ubuntu by the Update Manager. It downloaded the needed files and proceeded to install. However, during this install, the ram problem came up again and it forced me to reboot the computer. On startup, though, i couldn't launch Ubuntu. To me it seemed like some key files were deleted making it not start up (or rather replaced by half-baked versions of the upgraded version). I was pissed off at this point, so i once again messed around with the ram problem, and still didn't find a bad ram chip. 
 
After all this, i just tried to install Ubuntu 9.10 once again. However, i noticed that the mouse (i have a wireless mouse) had very choppy movement and wasn't smooth at all. After installing Ubuntu, i looked up on ways to fix this (ie. polling, acceleration/deacceleration), but they didn't quite work.
 
Because this was such an annoyance, i tried my best to fix this. I tried different mice (wireless optical, corded optical/ball), but the same problem persisted, so i concluded that it must be a system problem. This fact was reinforced when i deleted Ubuntu and installed Fedora on it. The mouse movement was fine on Fedora. I tried installing Ubuntu again, and succeeded but the mouse movement was still very choppy and not smooth.
 
At this point, i have no idea how to fix it. The ram problem i am 100% sure of fixing. The mouse problem is not because of this ram (i've thought of this and tried different ram combinations as well as single chips). I thought it was due to the Ubuntu Cd i got, but it was fine before. It is definately a system problem, but I'm out of ideas for the moment, so i thought to try the forum.
 
Any help? Is this a ram issue or software issue? That's my key struggle to find out.

---

### Post by Khary on 2010-05-07
I've installed Ubuntu 10.04, hoping it would fix my problem. However, that changed nothing.
 
When using my Ubuntu Live Cd with v. 9.10 on it, the mouse is still as slow as when i boot it up normally. Fedora and Windows do not have this mouse problem.
 
I am not quite sure what this could be. It has to be something to do with Ubuntu itself or maybe a mouse driver, as i've ruled out the ram problem or any other hardware problem for that matter.
 
Again, the mouse movement is not very smooth. I use a wireless Logitech mouse (not anything grandiose, like Razer), but in Ubuntu it seems to jump around and when i do circles on the screen, it skips pixels.
 
Since the mouse worked fine before, i am at a loss to explain this problem.

---

### Post by Khary on 2010-05-07
I am a gosh darn idiot. It seems that when i was messing around with the ram, i changed some bios settings on bootup to make it that my system had 'plug in and play' support. All i had to do was to disable that :/.

Oh man. 2 days of searching for an answer only to face slam into a wall due to sheer stupidity.

---

### Post by warfacegod on 2010-05-07
That's one of the damnedest fixes I've ever heard of.

---

