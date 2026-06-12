---
title: "Graphics Problem in Ubuntu 10.10? I'm not quite sure if I should call it that..."
date: 2010-11-29
forum: General Help
---

### Post by Dorakara on 2010-11-29
Hello everyone,
Since Ubuntu's install i have had graphical speed ups throughout the system. What I mean by this is that the graphics in games, and general desktop functions play at least twice as fast as normal. I assume this is a driver issue or a graphics card issue, but I don't know how to go about solving it. I have a Nvidia Ge Force 9500gt graphics card. If anyone can answer my prayers for answer I'll be quite grateful.

P.S: The challenge here is I have  installed linux yesterday, so I will need super simply put instructions as to how to fix it.

Thank you Muchly,
Dorakara

---

### Post by lrgmmc on 2010-11-29
did you install the nvidia drivers?

---

### Post by Dorakara on 2010-11-29
yes i did as soon as the install completed. i installed them from the additional drivers menu

---

### Post by lrgmmc on 2010-11-29
what drivers are you running?

---

### Post by Dorakara on 2010-11-29
NVIDIA accelerated graphics driver(version current) it was the recomended

---

### Post by lrgmmc on 2010-11-29
did you try the other one?

---

### Post by Dorakara on 2010-11-29
i have just tried it and the problem still exists

---

### Post by lrgmmc on 2010-11-29
what does running ```
gksu nvidia-settings
``` do?

---

### Post by Dorakara on 2010-11-29
it brings up the NVIDIA X server settings page
Operating System= linux-x86
nvidia driver version 173.14.28

---

### Post by lrgmmc on 2010-11-29
ok, time to get a little dirty. :) open run ```
gedit /etc/X11/xorg.conf
``` then copy it here. you might have a problem with the twin view feature.

---

### Post by Dorakara on 2010-11-29
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by lrgmmc on 2010-11-29
ok now run ```
gksu gedit /etc/X11/Xorg.conf
``` then add```
Option	"DynamicTwinView"	"false"
``` under ```
Option "NoLogo" "True"
``` and then save. you will need to reboot afterwards.

---

### Post by Dorakara on 2010-11-29
The problem persists after install

---

### Post by lrgmmc on 2010-11-29
ok now open display manager and check the resolution and refresh rates. try a couple.

---

### Post by Dorakara on 2010-11-29
where do i find the display manager?

---

### Post by lrgmmc on 2010-11-29
sorry i was working off memorie its called displays it is under system-->Preferances

---

### Post by Dorakara on 2010-11-29
it is not under my preferences window. is there perhaps another name in ubuntu 10.10?

---

### Post by lrgmmc on 2010-11-29
System-->Preferences-->Monitors

---

### Post by Dorakara on 2010-11-29
it appears that my graphics  driver does not support the necessary extensions  to use this tool. Do i want to use my  graphics driver vendor's  tool instead? <=message that popped up.

Also i was also wondering if this could also be a processor problem instead of a graphical problem?

---

### Post by lrgmmc on 2010-11-29
ok i'm not at my desktop to look through nvidia-settings but look through there and look at the display section should be able to adjust it there

---

### Post by Dorakara on 2010-11-29
changing the resolutions and refresh rates had no effect

---

### Post by lrgmmc on 2010-11-29
humm... i am kinda stumped at the moment. Sorry. i am going to subscribe to this thread and will post some more tomorrow. hope some others post as well. good luck and don't give up. there is an answer, just have to find it.

---

### Post by Dorakara on 2010-11-29
ok thank you for your time :) and also i had this problem a while back on windows and it was due to a virus. since thats not a possibility here im sure its something simple and silly I didnt even know affected the system XD

---

### Post by Dorakara on 2010-11-29
UPDATE:
New Information: It is not just graphics that are spend up its everything. The time (set at 8 o clock upon restart) is now reading 12:10 (2 hours fast). this  also happened in the preloaded games as well. the time diffence in game is roughly 10 linux seconds to every 1 real second. Hopefully this helps a solution to be reached sooner then expected :)

---

### Post by lrgmmc on 2010-11-30
ok in that case some more information will help. ie. running 64bit or 32. your processor, and motherboard.

---

### Post by Dorakara on 2010-11-30
my processor is a  dual core 3.1 ghz i believe, Its been a while since I've needed to check it for anything.
and  my motherboard i have no idea what it is, it has not been upgraded since I purchased my computer. Is there a linux command   to tell me the exact info you are searching for?

---

### Post by Dorakara on 2010-11-30
also it is 32 bit ubuntu 10.10

---

### Post by Tanner1294 on 2010-11-30
> **Dorakara said:**
> my processor is a  dual core 3.1 ghz i believe, Its been a while since I've needed to check it for anything.
and  my motherboard i have no idea what it is, it has not been upgraded since I purchased my computer. Is there a linux command   to tell me the exact info you are searching for?

That's all the information you need to know. This problem is actually very common among people with faster dual core cpu's. Everything is literally running twice as fast because both processors are working on the same things. (sounds stupid but it's true) Normally this affects Windows users who are playing older games meant to run on single core cpu's. Sadly, I don't know how to fix this on any Linux, but on Windows you goto task manager, and find the games process, right-click and click Set Affinity, then uncheck one of the processors so that it only uses one for the game =/ 

Hope this at least helps set you on the right track

---

### Post by Dorakara on 2010-11-30
UPDATE: I have been looking across a few forums for an answer. One person had a similiar problem to mine and it was fixed by disabling the program Cool and Quite. I wish to try this but I do not how to do this in linux.
Link to forum:
[http://www.nvnews.net/vbulletin/showthread.php?t=43460](http://www.nvnews.net/vbulletin/showthread.php?t=43460)

the difference is that the demo I have of doom 3 that I tried is in fast forward as well.

---

### Post by Dorakara on 2010-11-30
ah yes, I had that problem in windows a couple of times, but I could never set the affinity right to solve it :) thank you for the suggestion and hopefully linux pro can show me how to fix this in the Linux environment

---

### Post by lrgmmc on 2010-12-01
alright i would try this i know its a little old but hopefully it'll work.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=75281](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=75281)

---

### Post by Dorakara on 2010-12-01
I did the tests to see if this was my problem, unfortunately my pc did not have these spikes that is says should happen. Also unfortunately i tryed disabling AMD cool and quite but it did nothing to help. Also I checked my cmos clock to see if it was my motherboard battery going, and the cmos clock runs fine.

---

### Post by Dorakara on 2010-12-01
I was able to rifle through the system and find my exact processor as well:
AMD Athlon(TM) 64 X2 Dual Core Processor 6000+

---

### Post by Dorakara on 2010-12-01
Update:
I have now found that all ads in my browser, along with flash games have this issue. Perhaps a problem inside adobe flash? or this may just be a side effect of the initial problem

---

### Post by lrgmmc on 2010-12-02
wow. i dont know... i'm just shooting in the dark now. have you tried 64 bit version of ubuntu?

---

### Post by Dorakara on 2010-12-02
no i havent, my banwidth for this month is incredibly high so ill have to wait until later this month to try it, i was hoping this would be a quick fix XD

---

### Post by Dorakara on 2010-12-02
UPDATE=WTF???:
ok for no apparent reason my entire system works fine now. All games as they should etc. What happened?????????? i changed some settings in a game called freedroid RPG and it all worked. If we can figure out y im ready to mark this one solved :)

---

### Post by lrgmmc on 2010-12-03
congrats. just curius as to what settings you changed?

---

### Post by Dorakara on 2010-12-03
I changed the lazy graphics option. But wen i changed it back to what it was before it still worked. Is it possible Ubuntu just corrected its own problem? or that this may be an off and on thing?

---

