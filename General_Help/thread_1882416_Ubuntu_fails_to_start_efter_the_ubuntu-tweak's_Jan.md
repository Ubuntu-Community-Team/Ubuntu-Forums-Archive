---
title: "Ubuntu fails to start efter the ubuntu-tweak's Janitor froze."
date: 2011-11-17
forum: General Help
---

### Post by JimHolmstroem on 2011-11-17
Hi,

I installed and runned ubuntu-tweak-0.6 with what I think is the alpha version from "https://launchpad.net/~tualatrix/+archive/next" (I was directed to it from the ubuntu-tweak.com main page)
I was low on free space (since I dualboot on 80G SSD) so I thought I could free up some additional space with the janitor.
The Ubuntu 64bit clean installation was quite fresh and I updated to 11.10 on release date and I haven't had any stability issues (except for Flash, but how hasn't?)
So I went to the tab Janitor and marked almost everything showing up for removal.
(I think the execution order of the cleaning is like this)
-Apt cache (worked fine)
-Old Kernel (I think it worked fine, at least the kernels doesn't display in grub2, only the most current 3.0)
-Package configs <-- here is where the ubuntu-tweak froze midway (I watched the terminal output) and I was forced to xkill it after a while and didn't have any problems continuing  but i rebooted the system after a short while and found that Ubuntu wouldn't start anymore. After choosing the current kernel in grub2 the computer just goes blank (with the 1color ubuntu-purple)(a few times it became black with a blinking underscore)

I have scoured the Internet for possible solutions and tried fixing the problem from a liveCD trying to update/upgrade with apt-get and such, for a couple of hours now, with no success at all.

Does anyone know how I could fix this? or at least tell me what has happened? I hope i am not being a total newbie.

The Ubuntu system that crashed was Ubuntu 11.10 64bit (can easily give more details, don't really know what's relevant)

Thanks in advance :D

---

### Post by JimHolmstroem on 2011-11-17
Anyone got a clue/direction/google keyword?
I really need this to work again. 
I have just tried to make grub boot without doing the: "quite splash" 
but I don't think it did have any effect still just blank.

---

### Post by JimHolmstroem on 2011-11-17
Now I at least got rid of the splash image and got some feedback but the output is black text on black text-background (I can see it because the real background (not the text-background) is purple)
the only thing I see is that

Does anyone know how to change the text-color at init?

(I'm talkin' to myself on Internetz *forever-alone*)

---

### Post by MG&amp;TL on 2011-11-17
I would suggest booting from USB and backing up your home folder to somewhere before doing anything else. Copy your home folder to a memory stick or something. Then your configuration should stay he same if you need to reinstall.

---

### Post by JimHolmstroem on 2011-11-17
what I see: (- stands for blackbox)

--------------------
----------------------------------------------
-------------------------------------------------
----------------------------------------
--------------------------
-
-
-
------------------------------------                       ------
----------------------
--------------------------------------                     ------
-------------------
---------------------------
-----------------------                                    ------
--------------------------                                 ------
--------------------------                                 ------
-------------------------                                  ------
--------------------------------                           ------
----------------------                                     ------
-----------------                                          ------
-------------------                                        ------
---------------------------------------------
------------------------------------------------
-------------------------------------
-------------------------                                  ------
---------------------------------------
--------------------                                       ------
-------------------------------
---------------------------
* Checking battery state...-----                           [ OK ]
_ <--cursor blinking

---

### Post by MG&amp;TL on 2011-11-17
Hmmm...unusual. I would backup your stuff, then reinstall. I see no way around a hang like this. Wait for a bit to see if anyone else can do anything, but hanging at "checking battery state" isn't good. Sorry.

---

### Post by JimHolmstroem on 2011-11-17
Never mind, the text couldn't handle multispace,
to get the right color actually my computer went sleep almost and upon pressing the keyboard to wake the colors became black with white text:

Loading, please wait...
Begin: Lading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /script/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Runnings /scripts/init-bottom ... done.
fsck from util-linux 2.19.1
/dev/sda8 has been mounted 37 times without being checked, check forced.
/dev/sda8: 382807/864960 files (0.4% non-contiguous), 2827540/3455488 blocks
Checking disk drives for errors. This may take several minutes.
Press C to cancel all checks in progress


Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles [ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting bluetooth [ OK ]
 * PulseAudio configured for per-user sessions [ OK ]
saned disabled; edit /etc/default/saned
 * Starting System V runlevel compatibility [ OK ]
 * Starting CPU interrupts balancing daemon [ OK ]
 * Starting deferred execution scheduler [ OK ]
 * Starting regular background program processing daemon [ OK ]
 * Starting LightDM Display Manager [ OK ]
 * Starting ACPI daemon [ OK ]
fsck from util-linux 2.19.1
/dev/sda8 has been mounted 37 times without being checked, check forced.
/dev/sda8: 382807/864960 files (0.4% non-contiguous), 2827540/3455488 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles [ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting bluetooth [ OK ]
 * PulseAudio configured for per-user sessions [ OK ]
saned disabled; edit /etc/default/saned
 * Checking battery state... [ OK ]
_


Anyone got some ideas whats happening?

---

### Post by JimHolmstroem on 2011-11-17
thanks man, I should do that right away! :D
perhaps reinstalling tomorrow then

---

### Post by JimHolmstroem on 2011-11-17
And sorry I didn't ignore you i was busy rewriting what I saw on my other computer :)

---

### Post by MG&amp;TL on 2011-11-17
Well, it's checking your hard disk for some reason...presumably because janitor corrupted it in some way. I hve no idea why it's hanging at battery state-it should be "OK".

---

### Post by JimHolmstroem on 2011-11-17
Okey, hm, should I just try to wait really long? Think I have waited atleast 10-20mins, could those operations take longer or is it just corrupt, nothing to do about it?

---

### Post by BazookaAce on 2011-11-17
I'll never use any "janitor"/cleaning apps again after Computer Janitor managed to wipe half my system a month ago. Be VERY careful when using these types of apps.

---

### Post by JimHolmstroem on 2011-11-17
I never use them neither (from know one) :D
Thanks for the help guys :D

---

