---
title: "Question on how to install Nvidia drivers without losing menu?"
date: 2011-05-27
forum: General Help
---

### Post by TheLionHearted1 on 2011-05-27
Howdy everyone, thanks for taking the time to look at this.

Long story short, my question is about how to install Nvidia drivers without losing my menu. 
Slightly more specifically: When I go to install the drivers for my graphics card (Nvidia 7300 SE/ 7200 GS) under the 'Additional Drivers' menu in Administration, it does everything fine, wants to restart, and when it does, I have no menu, no bottom bar, nothing. The only thing on my screen is my wallpaper. (I'm using the gnome set-up, not Unity) 

Long story: For whatever reason, my Linksys adapter stopped working with Windows7. I dunno why, I tried everything, it's just not working. Yet when I boot into Ubuntu 11.04 x64 it works perfectly. HOW ON EARTH a Linksys device is working better out of the box on Linux than it does on Windows is profoundly beyond my level of understanding, but no complaints. Once I found out that Ubuntu can actually run World of Warcraft better than Windows, given the right adjustments... I removed Windows from my hard-drive post haste. I've gotten WoW *to run* on Ubuntu now, but it runs... horribly, like 1fps. Added the OpenGL text to the config.wtf file, and it got only very slightly less horrible, but I'd like to assume that having an actual driver for my graphics card would make the game playable.


Thank you for your input, also if anyone knows anything specifically about running WoW on Ubuntu, how to make it run better, any tweaks, literally anything you would think might be of help, I'd absolutely love to hear it, I'm really big into end game content so performance is very important to me.

-My computer's specs-
AMD Athlon 64 x2 5000+
3 gigs of ram
Nvidia 7300 SE/ 7200 GS
Ubuntu 11.04 x64.

---

### Post by wildmanne39 on 2011-05-28
> **TheLionHearted1 said:**
> Howdy everyone, thanks for taking the time to look at this.

Long story short, my question is about how to install Nvidia drivers without losing my menu. 
Slightly more specifically: When I go to install the drivers for my graphics card (Nvidia 7300 SE/ 7200 GS) under the 'Additional Drivers' menu in Administration, it does everything fine, wants to restart, and when it does, I have no menu, no bottom bar, nothing. The only thing on my screen is my wallpaper. (I'm using the gnome set-up, not Unity) 

Long story: For whatever reason, my Linksys adapter stopped working with Windows7. I dunno why, I tried everything, it's just not working. Yet when I boot into Ubuntu 11.04 x64 it works perfectly. HOW ON EARTH a Linksys device is working better out of the box on Linux than it does on Windows is profoundly beyond my level of understanding, but no complaints. Once I found out that Ubuntu can actually run World of Warcraft better than Windows, given the right adjustments... I removed Windows from my hard-drive post haste. I've gotten WoW *to run* on Ubuntu now, but it runs... horribly, like 1fps. Added the OpenGL text to the config.wtf file, and it got only very slightly less horrible, but I'd like to assume that having an actual driver for my graphics card would make the game playable.


Thank you for your input, also if anyone knows anything specifically about running WoW on Ubuntu, how to make it run better, any tweaks, literally anything you would think might be of help, I'd absolutely love to hear it, I'm really big into end game content so performance is very important to me.

-My computer's specs-
AMD Athlon 64 x2 5000+
3 gigs of ram
Nvidia 7300 SE/ 7200 GS
Ubuntu 11.04 x64.
Hi, was there 2 drivers listed when you activated the nvdida driver? if so try the other one. Did you set up the cube or any desktop effects?

---

### Post by TheLionHearted1 on 2011-05-28
I tried both of them with the same problem.

And no, I haven't touched any of the desktop effects yet.

---

### Post by wildmanne39 on 2011-05-28
> **TheLionHearted1 said:**
> I tried both of them with the same problem.

And no, I haven't touched any of the desktop effects yet.Hi, in nvidia setting manager make sure that vsync to blank is not checked. It sounds like your install might not have completed,did you upgrade or do a clean install?

---

### Post by linuxinstalledfromhdd on 2011-05-28
> **TheLionHearted1 said:**
> 

Thank you for your input, also if anyone knows anything specifically about running WoW on Ubuntu, how to make it run better, any tweaks, literally anything you would think might be of help, I'd absolutely love to hear it, I'm really big into end game content so performance is very important to me.

-My computer's specs-
AMD Athlon 64 x2 5000+
3 gigs of ram
Nvidia 7300 SE/ 7200 GS
Ubuntu 11.04 x64.

I would try to follow the posted recommendations for installing WoW with OpenGL in Ubuntu over here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Also for gaming I've been really successful at installing WinXp in Virtualbox 4, and playing games with that from inside of Ubuntu. 

[http://www.webupd8.org/2010/12/install-virtualbox-40-stable-in-ubuntu.html](http://www.webupd8.org/2010/12/install-virtualbox-40-stable-in-ubuntu.html)

That's my own preferred way for some specific games that will not render properly in Wine for whatever reason.

---

### Post by TheLionHearted1 on 2011-05-28
> **wildmanne39 said:**
> Hi, in nvidia setting manager make sure that vsync to blank is not checked. It sounds like your install might not have completed,did you upgrade or do a clean install?

Could you point me in the direction of where I might find the Nvidia Settings Manager?

It was a clean install.

---

### Post by TheLionHearted1 on 2011-05-28
> **linuxinstalledfromhdd said:**
> I would try to follow the posted recommendations for installing WoW with OpenGL in Ubuntu over here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Also for gaming I've been really successful at installing WinXp in Virtualbox 4, and playing games with that from inside of Ubuntu. 

[http://www.webupd8.org/2010/12/install-virtualbox-40-stable-in-ubuntu.html](http://www.webupd8.org/2010/12/install-virtualbox-40-stable-in-ubuntu.html)

That's my own preferred way for some specific games that will not render properly in Wine for whatever reason.


I didn't even think about running it through a VM, that's actually a genius idea!

Where might I find Virtualbox 4? Ubuntu software center?

---

### Post by fooman on 2011-05-28
> **TheLionHearted1 said:**
> Could you point me in the direction of where I might find the Nvidia Settings Manager?


system > administration > NVIDIA X Server Settings

---

### Post by wildmanne39 on 2011-05-28
> **TheLionHearted1 said:**
> Could you point me in the direction of where I might find the Nvidia Settings Manager?

It was a clean install.
Hi, go to administration and it is in there, I think it only appears after you install your drivers for your video card.

---

### Post by TheLionHearted1 on 2011-05-29
Alrighty, I'll give it a whirl.

If for whatever reason it doesnt work, and I need to boot into safe-mode and uninstall the driver, how would I do that?

Do you just press F8 while it boots, similar to Windows or is there some other way?

---

### Post by wildmanne39 on 2011-05-29
> **TheLionHearted1 said:**
> Alrighty, I'll give it a whirl.

If for whatever reason it doesnt work, and I need to boot into safe-mode and uninstall the driver, how would I do that?

Do you just press F8 while it boots, similar to Windows or is there some other way?Hi, this link will tell you how to boot into recovery mode.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by TheLionHearted1 on 2011-06-01
I've gotten everything working now, thanks for your time.

---

