---
title: "Emulators Not Working"
date: 2010-02-07
forum: General Help
---

### Post by joelandsonja on 2010-02-07
The problem I have is that I am not able to get ANY of my Emulators to work in Ubuntu.

I have been trying for months now, but there isn't a single reliable emulator that works on Ubuntu. 

There always seems to be problems with lagging, and sound issues that never seem to get resolved. 

This is beyond frustrating because Gaming is the one thing i need to have on my computer, yet it is the only thing I'm not able to get working. 

Do any of you know of any alternative suggestions to fix this problem?

I have tried EVERY available emulator for both Windows (Used on Wine) and Ubuntu. 

Is there some kind of general setting for Wine that I am overlooking?

Here are a list of Consoles I want to play:

- Super Nintendo
- Nintendo
- Sega Genesis
- Sega Master System
- Nintendo 64
- Playstation
- Gameboy Advanced and Original

Someone please help me!

---

### Post by joelandsonja on 2010-02-07
Also, if anyone knows of a reliable M.E.S.S. emulator for windows in .deb format I would appreciate it.

I don't usually have much luck with M.E.S.S. emulators since you usually need a PHD to get the thing working, but I thought I would give it a try.

---

### Post by switch10 on 2010-02-07
I have used both zsnes for snes, and mupen 64 for nintendo64 without any problems.  I would not use wine to run an emulator, that will make things slow, and laggy even on a higher end system.  

If gaming is a big thing for you, maybe consider using Windows for that.

You cant get zsnes to work?  Are you getting some kind of error?  It is extremely easy to install and use.

---

### Post by blueshiftoverwatch on 2010-02-07
> **joelandsonja said:**
> The problem I have is that I am not able to get ANY of my Emulators to work in Ubuntu.
If your using a 64 bit system, my experience is that emulators on Linux don't run as well. It's also impossible (most of the time) to even get 32 bit emulators to compile on a 64 bit system. Which severely limits your options.

---

### Post by joelandsonja on 2010-02-07
Hmm ... using a 64 bit system might be the problem. 

However, I actually have Ubuntu 32 bit installed ... but I'm not sure if it makes a difference.

I have tried all of the generic emulators available on Linux, but none of them are worth keeping. They all lag terribly, have sound issues, or flat out refuse to play certain games.

I suppose using Virtualbox would be the best solution, but I am looking for a way to disable the Internet permanently, and the last time I tried this I couldn't figure it out. Also, Virtualbox had a lot of problems recognizing USB drives.

Would anyone know of a solution to this?

---

### Post by switch10 on 2010-02-07
> **joelandsonja said:**
> Hmm ... using a 64 bit system might be the problem. 

However, I actually have Ubuntu 32 bit installed ... but I'm not sure if it makes a difference.

I have tried all of the generic emulators available on Linux, but none of them are worth keeping. They all lag terribly, have sound issues, or flat out refuse to play certain games.

I suppose using Virtualbox would be the best solution, but I am looking for a way to disable the Internet permanently, and the last time I tried this I couldn't figure it out. Also, Virtualbox had a lot of problems recognizing USB drives.

Would anyone know of a solution to this?

If you have a 32 bit OS installed, you are on a 32 bit system.  So your problems are not because your computer has the capability of running a 64 bit OS.  

to disable a network in virtualbox, click on setting>network and uncheck "enable network adapter".  No more internet.  I've included a screenshot.

USB works fine in Virtualbox.  You have to get the version from the virtualbox website, not the OSE version found in synaptic.  Then add yourself to the virtualbox group.  

If I were you though, I would work on getting your problems fixed with the native Linux emulators.  I have installed them on several computers, on both architectures.  It takes some configuring, but its not that hard.  Do some google searches of your exact problems.

I also included a screenshot of my audio settings in ZSNES.  Maybe they will help.

---

### Post by joelandsonja on 2010-02-07
Wow, thanks for the help ... I am actually in the process of reinstalling Virtualbox on my system, but I came to a bit of a snag during installation. 

I realize Virtualbox installs Windows within the program, but the Windows installation is asking me to format the 40GB of space I allocated to the device, and I don't remember it asking me this before ... would this be normal, considering the fact that I don't want to lose any information on my harddrive?

I'll Include a Screenshot of What I mean:

---

### Post by TriadHonor on 2010-02-07
I'm currently using **ZSNES** 64bit under Ubuntu Karmic, 64bit.

I also try Karmic in VMware but there I experience some troubles because the hardware is not well supported.

So it depends on your system maybe, not directly from 32bit or 64bit.
Obviulsy, if you force the 32bit to work on 64bit it don't works...

You are on 32bit, so now we need to know something about your hardware.
Have you installed your graphic driver correctly ?

Can you use things like Compiz or some 3D games ?

Sound works ?

Tell us more, please.

---------------------------

Second, I'll try to provide a list of emulators you can use, so please, visit these links:

**SNES & PS1**
[http://www.zolved.com/synapse/view_content/28038/How_to_install_some_popular_gamesemulators_on_Ubuntu](http://www.zolved.com/synapse/view_content/28038/How_to_install_some_popular_gamesemulators_on_Ubuntu)


**DOXBOX, NES & SNES **
[http://linuxondesktop.blogspot.com/2007/03/playing-classic-games-under-ubuntu.html](http://linuxondesktop.blogspot.com/2007/03/playing-classic-games-under-ubuntu.html)

(Updating tomorrow )

---

### Post by joelandsonja on 2010-02-07
> 
You are on 32bit, so now we need to know something about your hardware.
Have you installed your graphic driver correctly ?

Can you use things like Compiz or some 3D games ?

Sound works ?

Tell us more, please.

I'm pretty sure the graphics driver is working properly, I am able to actually play some games in 3D and have sound as well, so I don't think that would be the problem.

Zsnes is now working (Thank you!) but the other emulators aren't. 

Also, could someone let me know if the formatting process is normal when trying to install windows on Virtualbox?

Thanks again!

---

### Post by switch10 on 2010-02-07
yes, that is fine.  You've alloted 40GB for virtualbox to use.  Windows wants to partition this as NTFS.

What problems are you having with mupen64?  I have that installed and working perfectly on this machine as well.

---

### Post by joelandsonja on 2010-02-08
For some reason Mupen 64 is very choosy with the roms it will play, so there are many games I am not able to play. (As opposed to Project 64) It also has a problem finding my gamepad as well ... and I have a very common gamepad. (Logitech Dual Action) I have tried adjusting it many times, but it doesn't want to work. 

I'll give virtual box another try to see it that works ...

---

### Post by TriadHonor on 2010-02-08
I'm happy for the SNES :-)

Well, so now I'm looking for more emulators, I'll write you as soon as I find something.

---

