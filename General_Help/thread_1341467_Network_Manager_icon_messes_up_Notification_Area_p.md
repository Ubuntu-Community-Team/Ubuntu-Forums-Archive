---
title: "Network Manager icon messes up Notification Area panel applet."
date: 2009-11-29
forum: General Help
---

### Post by bshosey on 2009-11-29
This is my 3rd post on this. I have tried everything I can think of. I have uninstalled Indicator-applet, Indicator-applet-session, this fixed it for about 1 week then came back. Then I uninstalled ubuntu-one packages and this fixed it for about 2 weeks. Reinstalling Network-Manager and Network-Manager-Gnome will fix it for 2-3 days. Changing the theme has no effect on this. Now every machine that I have, that is ubuntu the Network Manager screws up. It will now show an icon that is not Network Manager. I will have a duplicate icons of speaker or blue-tooth, battery but not the Network Manager icon. When this happens I can not do anything with Network Manager. I have to remove the Notification-Area panel applet from the panel and re add it. I have been fighting this from day one of the 9.10 release. Some one please help. I am getting very frustrated. I have had Driver issues, Xorg issues, Wireless issue previous releases that I have been able to resolve or at least get help on. I have not gottem much of a response on this issue from people. I love ubuntu. I do not know how to resolve this issue. It is really annoying the heck out of me. 64 bit and 32 bit does this with fresh install and upgrade. I have Intel video and ATI video cards.

I have 2 ubuntu servers both have ubuntu-desktop installed, I know bad monkey! (No problems because no Network-Manager )
I have one Dell Latitude D630 laptop not hooked up to external monitor, Intel Video (My DJ workstation, it has this problem)
I have one Dell Latitude D630 laptop hooked up to external monitor, Intel Video (My VJ workstation, it has this problem )
I have one Dell Latitude D420 laptop not hoked up to external monitor, Intel Video (Travel to work system, it has this problem )
I have one Dell Inspiron 1721 laptop not hooked up to external monitor, ATI Video (My every day home personal one, it has this problem, This system is the one that I have had problems with previous releases but not this issue)
All are common dell systems. I know that is a lot of systems but they are used for specific things.


Please help. I use these systems a lot most for fun but I do several projects with them. I love ubuntu and am hoping to get more involved with it.

---

### Post by solemnavalanche on 2009-12-11
Aha! I am having the same problem. I can't help you but I thought you'd appreciate the validation.

Unfortunately this hasn't been the best Ubuntu release for me; this is only the most minor of the many problems Karmic has had on my computer. I'm on the verge of reinstalling Jaunty.

Edit:

Someone on the bug report posted this kludgy but effective workaround. 

Create a script with the following lines:

#!/bin/bash
killall gnome-panel

Go to System->Preferences->Startup Applications and add the script.

The script kills the panel, which restarts automatically. Because it happens right at startup, the effect is quite invisible. Works for me, anyway.

---

### Post by bshosey on 2009-12-11
I am only having 2 problems with Karmic now. Rhythmbox not cross fading betwean mp3s on the same album. And the crazy network manager icon problem. Other wise I really like karmic.

---

### Post by j7%&lt;RmUg on 2009-12-11
Its not really a big issue, just seems to be a small unfixed bug, all it does for me is make the icon disappear half the time.

It should only annoy those people who never use the terminal for network management stuff.

---

### Post by bshosey on 2009-12-11
Question about that script. Do you really need the script. Could not just add the command to the startup apps or am I missing something there. The reason I ask this is because it is even an easier solution to walk someone through.

---

