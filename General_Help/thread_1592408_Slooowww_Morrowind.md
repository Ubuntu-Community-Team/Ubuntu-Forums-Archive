---
title: "Slooowww Morrowind"
date: 2010-10-10
forum: General Help
---

### Post by Deltanu Zero on 2010-10-10
Greetings,

There is this ancient game (from 2002) that I enjoy to play, and it's called Morrowind. I used to play it on winblows but that OS blew up. (no really, it did. as much as software can explode.)
I happily installed Ubuntu 10.04 LTS from a CD I had already made earlier. I wanted to dual boot, but as windows decided to cease function...

anyhow, this weekend I tried to get Morrowind working in Ubuntu.
We'Re talking only the original Morrowind (no expansion packs) with no mods except for the unofficial patch. 
I did everything as explained at [http://forums.fedoraforum.org/archive/index.php/t-156033.html](http://forums.fedoraforum.org/archive/index.php/t-156033.html)
Also, I use the latest version of Wine.

**The Problems in my quest to get Morrowind**
first thing I noticed: at first the OS doesn't seem to recognize my CD station. not even the morrowind NRG I mounted with Furius ISO Mount. sure I could install just fine, but the morrowind.exe insists on checking the presence of a CD and refuses to continue without. 
my attempts at NoCD-ing failed so I fiddled around a bit, and EVENTUALLY managed to get a virtual drive recognized. I'm new to linux and pretty much not experienced so yeah.

cue the next problem. Morrowind.exe launches, that's what it does. after startup it happily starts to render the opening credits. ("Bethesda Softworks" etc)
At two frames per second. with the sound distorted to match the graphics speed. seriously. when it finally comes at the loading screen everything looks normal, until that finishes. cue the next ultra-slow slideshow of frames until the main menu pops up. 
in that menu, the mouse works at about the same pace as the rest of the stuff so far. I had great trouble selecting "New" (as in new game) cause the pointer would only move 2 seconds after moving the mouse. 
persistant as I am, I managed to start a new game. the intro movie was of the same quality as the previous stuff. the game than loads normally, and puts me in the starting position. 
guess what? the mouse and keyboard controls seem to take several seconds to travel through the wire into the computer and towards the screen. one key at a time. (typing in character name: D... wait 3 seconds... E.... wait 3 seconds... L... etc until it spelled Deltanu. I typed at normal speed.) graphics look nice though, and the sound works perfectly fine, and at normal speed. still not enough for a playable game.

my Morrowind is slow. very slow. since it is also the opening credits and the menu that are affected, not just the gameplay, I think my system specs aren't the problem. (it ran fine in windows with the same hardware)
maybe the drivers for my graphics card? (an Intel Corporation 82915G/GV/910GL Express chipset family from DELL) I doubt it since it does render the starting position quite nicely.
as I said, I am using the latest version of Wine. I tried with and without pixel shader enabled, the result was the same. 
I am playing the game in windowed mode, not fullscreen. although the width/height have been adjusted to match my monitor's dimensions sans the top/bottom bars of Ubuntu. 

somehow my game is running in slow mode, with both the input and output happening at very slow pace. can anyone help me to get it going at a more decent speed?

---

### Post by Deltanu Zero on 2010-10-12
Any idea's yet?

---

### Post by yetiman64 on 2010-10-12
Some info on Morrowind under Wine, (unpatched cd version gets a gold rating)

[--Wine HQ database entry--]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1015") 

Also have you considered trying PlayOnLinux? It has a good list of games including"The Elder Scrolls III-Morrowind" and will automatically download and install the appropriate Wine version for a particular game, this feature may be of some help to you. A version of PlayOnLinux is available in the repositories (may not be the lastest version though).

[--PlayOnLinux--]("http://www.playonlinux.com/en/")

Hope this helps you.

---

### Post by Deltanu Zero on 2010-10-13
As you suggested I tried PlayOnLinux.
first I uninstalled morrowind and wine. after a reboot (cause I like doing reboots after stuff) I opened terminal and typed

sudo apt-get install playonlinux

which actually worked =)
it installed PlayOnLinux and Wine 1.1.42
I proceeded by mounting my morrowind .nrg and using the POL interface to install. this went smoothly, and I have faith that it works.
except that I cannot test that assumption. 

when I try to run morrowind I get the "No CD/DVD drive detected on this computer" message even though I have the image mounted. (powered by Furius ISO mount)
the installation required me to tell POL where the (virtual) CD folder was, which I did. so it can install, but morrowind fails to recognize it as a drive.

any idea on how to get it recognized?

when I go Applications>Wine>configure I have the virtual drive listed as E: <name> with the type set to CD-ROM. this did it for the previous installation. 

thanks so far ;)

---

### Post by spcagigas on 2010-10-15
What video driver are you using?  I had the same issue with Morrowind using an ancient Nvidia GE Force video card.  Installing the restricted drivers for the video card enabled the 3D processing, after which Morrowind ran *quite* nicely.

---

### Post by Deltanu Zero on 2010-10-28
PlayOnLinux didn't solve anything, so I uninstalled morrowind, POL and wine. then after
sudo apt-get install wine
I installed morrowind again, and with pixel shader turned off the intro movie is actually smooth! gameplay becomes somewhat doable but still very slow. the mouse pointer isn't moving smoothly in the game, and the graphics speed isn't affected (much) by the graphic settings like view distance. 

> **spcagigas said:**
> What video driver are you using?  I had the same issue with Morrowind using an ancient Nvidia GE Force video card.  Installing the restricted drivers for the video card enabled the 3D processing, after which Morrowind ran *quite* nicely.

That could be a good point.
I found [http://ubuntuforums.org/showthread.php?t=646064](http://ubuntuforums.org/showthread.php?t=646064)
which is about the same card as mine. 

however thus far, things aren't cooperating that much. 
system > administration > Hardware Drivers gives a blank screen saying "no proprietary drivers are in use on this system" with the only options to click "Help" (not so helpful) and "close" 

also, in /etc/X11 there is no xorg.conf.
there is a xorg.conf.failsafe though, which reads
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

any idea's?

---

### Post by Deltanu Zero on 2010-11-13
Anyone know how to fix this driver thing?

---

### Post by raptherenegade on 2011-03-12
> **Deltanu Zero said:**
> Anyone know how to fix this driver thing?

No I don't, but I sympathise: I'm trying to get Morrowind going again on my laptop (used to work with almost no bugs): all I have is an internal sound card and monitor card. Now I'm having problems. When I installed (from setup.exe) I was told that some installation support files were missing. But I ran Morrowind, only with sound and slight lag issues. 
I'm told by the tech support info file that sound card issues are a major source of slow or crash-prone play, but I am really helpless when it comes to knowing about hardware acceleration. Sorry for the rant, you're troubles are no doubt greater than mine.

---

