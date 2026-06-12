---
title: "interesting problems with dual monitors"
date: 2010-03-04
forum: General Help
---

### Post by omega52390 on 2010-03-04
i started this on wine forums originally but through discussion we came to the decision that this belonged on ubuntu forums

ok so i will start off with some specs to help you, help me, help us all. 
i am running ubuntu karmic 64bit, corei7, 6gigs ram, and 2 nv gts 250s(wont be able to run sli until they add dual monitor sli support to linux drivers) ignore the fact that i have a second card its not used in linux. but my big problem lies somewhere in my two monitors running twinview (both monitors resolutions are 1680x1050). when i say games i mean any source engine game (hl2 portal css etc.) 

whenever i try to play a game it different things will happen depending on a few setting with wine config. if everything is set to initial defaults in graphics tab of wine config (only the desktop integration stuff enabled) then the game will start up and it is working but you can only see half of the screen, this is because for whatever reason the game is forced to run at a resolution of 3360x1050 and is not expanding across both screens if i go in game and try to change the resolution it gives me no options other than what it is already set to if i set it to windowed mode i still get no options other than 3360x1050 but the game will span both screens 

if i disable the desktop integration in wine config then the game will span both screens in full screen and windowed mode but i still cant change the resolution. 

my last option is to run the games in windowed mode set to 1680x1050 via wine config. this option has worked for me with another game that had a similar problem. i just went back and tested halflife2 and it works this way (introvideo doesnt) although something wasnt right it looked like it was running at dx8 even though it said it was running dx9 however i dont know much about this kind of stuff (i hope i make sense here: the polygon count and texture resolution looked to low for my settings) the video of breen on the screen in the station looked more pixelated than it should have and when people talked their mouths looked jumpy and jagged like an older game would. in portal once i start a game i just get a black screen with audio. the intro commands like the thing on the right that tells you about WASD shows up and so does an unmodifed targeting reticle but nothing else and i cant move 

first thing done was we checked xrandr
```
Screen 0: minimum 3360 x 1050, current 3360 x 1050, maximum 3360 x 1050 
default connected 3360x1050+0+0 0mm x 0mm 
   3360x1050      50.0* 
```

so we figured out that after looking at this section of xorg.conf
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: nvidia-auto-select +1680+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
```
that nvidia-settings was not doing something correctly when it configured xorg.conf. now even though i can understand all of this pretty well editing it is not something im confident about.
the metamodes option needs more but i dont know how to fix it. one guy mentioned something about sax2 but thats a suse thing so i was wondering if ubuntu had something equivalent to sax2

---

