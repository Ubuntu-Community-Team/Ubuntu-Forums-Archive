---
title: "Running XP in a shell in Ubuntu 10.10"
date: 2011-04-18
forum: General Help
---

### Post by Hamani on 2011-04-18
Hey guys. 

I think this is the right place to post this, but if not just let me know. 

Basically I want to be able to run XP in a shell inside the Ubuntu environment (as opposied to just having duel install. 

Is this possible? Stable? Realistic?

Its only for gaming really as I don't have all that much luck with Wine. Any advice or help will be greatly appreciated. 

Ga.

---

### Post by mendhak on 2011-04-18
Two answers:

First - if you want to run Windows, you can download and install VirtualBox.  VirtualBox allows you to install an operating system within your predefined parameters.   So you'd install Ubuntu, log in to Ubuntu, but run the VirtualBox application to start Windows XP/Windows 7 within another window.  (It does do fullscreen and seamless modes too).

Second - if you're interested in gaming, you will want to get playonlinux.  You said you haven't had luck with Wine.  PlayOnLinux does the Wine download and prefixing for you, and it has a list of supported games which work.  It depends on the game you want to play, though.  Some popular games do work and others are hit and miss (for which you'll want your Windows installation).  Remember that in VirtualBox, you define the amount of memory available to the guest OS (in your case, Windows is the Guest OS) and so your gaming performance is determined by those resources.  To be a bit more specific, I've been able to get Portal, HL2, NWN, WoW, Amnesia, MineCraft and Assassin's Creed working on Ubuntu using PlayOnLinux.

---

### Post by 3Miro on 2011-04-18
With VirtualBox you can only play non 3D games. PlayOnLinux is easier to setup then wine, if this is the problem, then POL may work for you.

---

### Post by Hamani on 2011-04-18
Thanks for the replies guys. 

I'm not worried about 3D and performance. I'm talking real old-school games like Red Alert 1 and Seven Kingdoms. 

Is PlayOnLinux free software? I've heard of payable but better versions of wine ... but paying for software kind of defeats the point of linux in the first place for me.  

For VirtualBox what kind of parameters do you mean? And what would seamless modes mean? I'm not completely useless with computers I'm just still learning lots. 

Ga.

---

### Post by mendhak on 2011-04-19
Yes, PlayOnLinux is free.  Think of it as a front end interface to help you configure Wine.  You should be able to find it in Synaptic Package Manager. 

About VirtualBox - when you define a new guest OS, you can define things like "Give it 2GB of RAM" or "Let it use just 1 core out of my 4 cores".  Those are the parameters that are used to configure the environment your Windows guest OS will run in and so can affect how your games appear.  If they are old games as you say then you shouldn't need to supply it with too many system resources.

However, Wine is still a viable option for you.  You can install Wine and then attempt to run the installer for your games, that should be it.

---

### Post by kiyop on 2011-04-19
VMwarePlayer is also a virtualization tool.
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)
I use it to run Windows XP (Guest) on my Ubuntu (Host).

---

