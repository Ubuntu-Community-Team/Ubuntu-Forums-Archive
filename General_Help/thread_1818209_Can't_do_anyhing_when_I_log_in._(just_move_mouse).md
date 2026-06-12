---
title: "Can't do anyhing when I log in. (just move mouse)"
date: 2011-08-04
forum: General Help
---

### Post by Jack14112 on 2011-08-04
[COLOR=black][FONT=Verdana]Hey everyone,[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I am very new to Ubuntu so sorry if I don't know what I'm talking about.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Basically I installed Ubuntu 11.4 on an oldish computer. I loaded up fine, everything was working. Then I was prompted to (I think) activate my nVidia graphics card drivers. When I restarted and logged in the whole desk top was unresponsive, I can move that mouse but that&#8217;s about it. I have tried reinstalling Ubuntu but I keep getting the same problem. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]If you need any more information just ask.[/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Any help would be much appreciated,[/FONT][/COLOR]
 
Jack.

---

### Post by Jack14112 on 2011-08-04
Hey everyone,

I am very new to Ubuntu so sorry if I don't know what I'm talking about.
Basically I installed Ubuntu 11.4 on an oldish computer. I loaded up fine, everything was working. Then I was prompted to (I think) activate my nVidia graphics card drivers. When I restarted and logged in the whole desk top was unresponsive, I can move that mouse but that’s about it. I have tried reinstalling Ubuntu but I keep getting the same problem. 
If you need any more information just ask.

Any help would be much appreciated,

Jack.

---

### Post by Jack14112 on 2011-08-04
Anyone?

---

### Post by coffeecat on 2011-08-05
Welcome to the forum.

There have been reports of some older nvidia cards being problematic in 11.04, so first question: which nvidia GPU do you have?

Just to clarify what you have experienced - when you first installed Ubuntu 11.04 you were able to boot into a desktop with panels top and bottom and with a "Applications - Places - System" menu top left. Am I correct? And were you able to use the GUI OK - open and run applications, and so on? That is the classic gnome desktop, by the way. If so, you were probably greeted with a message first time saying that your hardware wasn't sufficient to run the Unity desktop.

After you installed the proprietary nvidia driver you say that when you rebooted the desktop was unresponsive but that you are able to move the mouse cursor. Is there anything else on the desktop apart from the mouse cursor? Any panels top or bottom? My guess is that the system is trying to open the Unity desktop and failing. If you don't know what the Unity desktop looks like, click on the first link in my sig.

Try this: at the log in screen enter your account name, but before you type in your password, click on the popup at the base of the screen and choose "classic". Now enter your password and, hopefully, you'll be taken to the classic desktop. That's not Unity but at least it will something usable from which you can do some investigation.

I have a couple of options for you to try, but first let's see if you can get to the classic desktop and don't forget to post details of your nvidia card.

---

### Post by vlbaindoor on 2011-08-05
> **Jack14112 said:**
> [COLOR=black][FONT=Verdana]Hey everyone,[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I am very new to Ubuntu so sorry if I don't know what I'm talking about.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Basically I installed Ubuntu 11.4 on an oldish computer. I loaded up fine, everything was working. Then I was prompted to (I think) activate my nVidia graphics card drivers. When I restarted and logged in the whole desk top was unresponsive, I can move that mouse but that&#8217;s about it. I have tried reinstalling Ubuntu but I keep getting the same problem. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]If you need any more information just ask.[/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Any help would be much appreciated,[/FONT][/COLOR]
 
Jack.

I have had similar problems - I have Asus P5Q motherboard and a Nvidia card with dual monitors. But if I install and activate the nvidia drivers I have the same problem as you are describing.

I had better success with Kubuntu 11.04 but the sound card did not work properly - but now I am using UbuntuStudio 64bit version (11.04) and touch wood everything seems fine.

Even on UbuntuStudio64 that I have now, my system says (If I did System -> Administraion -> Additional Drivers) something like Nvidia Driver installed but not in use but I can run the 'nvidia-settings' application and it seems to think everything is working fine - and more importantly I feel everything is working fine. Both of my display panels are working as I want them.

---

### Post by s.fox on 2011-08-05
Please do not create duplicate threads. Thank you.

Threads Merged.

---

### Post by coffeecat on 2011-08-05
> **vlbaindoor said:**
> Even on UbuntuStudio64 that I have now, my system says (If I did System -> Administraion -> Additional Drivers) something like Nvidia Driver installed but not in use but I can run the 'nvidia-settings' application and it seems to think everything is working fine - and more importantly I feel everything is working fine. Both of my display panels are working as I want them.

That message - "activated but not in use" - is a known bug. If it is activated, it is in use. You can ignore it.

---

