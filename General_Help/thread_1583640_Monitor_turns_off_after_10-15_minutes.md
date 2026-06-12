---
title: "Monitor turns off after 10-15 minutes"
date: 2010-09-28
forum: General Help
---

### Post by GaldorT on 2010-09-28
I've read many posts about other people having this issue and I can't seem to find one that is the same problem I am having.

I'm totally new to ubuntu and linux as well for that matter, so any help will be greatly appreciated.

Basically I wanted to give linux a try and started doing some research and liked everything I read about ubuntu. I went to the website and used the wubi (I think that was what it was called) to install ubuntu. Now when I boot my computer it asks me which operating system I would like to use. I navigate to ubuntu and press enter and it starts up with no problems what so ever. 

At first I was really surprised with how easy the installation was and how great everything was going, however. After looking around for about 10 minutes, the screen abruptly went black and then my monitor had a small blue box on it with "No input" on it before the light went from blue to orange. I tried hitting every combination of keys I could think of and in the end had to do a hard restart.

Long story short...every time I use ubuntu my monitor shuts off after about 10-20 minutes, regardless of what activity I am doing. I've tried going to  /apps/gnome-power-manager/timeout/ to make sure that sleep_display_ac was set to 0 (it was), I've turned off power management using the power manger under preferences. No matter what I have tried, it continues to be a problem.

Any help would be GREATLY appreciated as I really would like to give ubuntu a complete trial, but as is...its virtually impossible to get into anything more than playing a game of Mahjong :P Thank you in advance.

---

### Post by mastablasta on 2010-09-28
Wubi installer:
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
 
**Any gotcha?**
 
Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.
-----
 
Could be that something is messing up suspend/hibernation.
 
Does it do the same if you boot from live CD and "play" with it for 20 mins?
 
If you want to use windows along with Ubuntu i suggest a propper dual-boot install where you will split your Hard disk and install ubuntu on new partition totally separated from windows.

---

### Post by GaldorT on 2010-09-28
I haven't given the live CD a try, but after reading what you typed and alot of the link you provided, I think I'm going to give a proper partition/dual-boot a try.

The only other thing I might try first is to disable the hybernation/screen saver in windows before rebooting, as the ubuntu is actually installed in a folder in windows.

Thanks again for the speedy response, and I'll let post back with anymore information.

---

