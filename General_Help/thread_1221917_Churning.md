---
title: "Churning"
date: 2009-07-24
forum: General Help
---

### Post by BobLand on 2009-07-24
Lately, my machine is behaving like Windows 95.  I turn the computer on and it churns and churns, sometimes up to 5 minutes.  I have Thunderbird, Sunbird and Firefox set to automatically boot when the system comes on.

I suspect the culprit is Firefox as it has been behaving very badly since I upgraded to Jaunty.  Everytime I quit FF it says Force Quit.  Sometimes it requires me to select the button, other times not.

After running for a while FF refuses to play any videos.  I usually have to restart FF, then everything is OK.

Suggestions?

---

### Post by tripolitan on 2009-07-24
Any idea what hardware you're using? start with RAM/Processor/HD speed

---

### Post by Insightfill on 2009-07-24
> **BobLand said:**
> I suspect the culprit is Firefox as it has been behaving very badly since I upgraded to Jaunty.  Everytime I quit FF it says Force Quit.  Sometimes it requires me to select the button, other times not.

Sounds like a memory leak in one of the Firefox plugins.  Can you provide a list?  Try disabling a few of them, restart Firefox, and see how things behave after a few hours.

The fact that you are asked to force quit, but that it sometimes goes away by itself hints that Firefox is taking a while to shut-down, probably due to rampant memory use.  There are a handful of "about:config" settings to get Firefox to use less memory.

---

### Post by BobLand on 2009-07-25
I'm running Jaunty on a Dual-Core 2G with 2G RAM.  My add-ones are:
Adobe Reader 9.1
Cooliris
Default Plugin
Demo Print Plugin for unix/linux
DivX Rrowser Plugin
gecko-mediaplayer 0.9.4
IcedTea Java Web Browser Plugin
QuickTime Plug-in 7.4.5
RealPlayer 9
Shockwave Flash
Windows Media Player Plug-in

Most of these I probably don't use so I will remove them and see if that helps.

---

### Post by tripolitan on 2009-07-26
Keep these:

Adobe Reader 9.1
Default Plugin
DivX Rrowser Plugin
QuickTime Plug-in 7.4.5
RealPlayer 9
Shockwave Flash
Windows Media Player Plug-in

and make the browser's home about:blank and remove the startup tabs. I believe this should speed things up quite a bit. You can also try opening a terminal window and type "top" to see the cpu/ram consumption per application. (stop top from running by ctrl-c)

---

### Post by BobLand on 2009-07-26
I kept what you said and moved everything over to 3.5.  No more churning.  Yes, 3.5 is buggy but more stable in my system then 3.0.

---

### Post by tripolitan on 2009-07-27
This may not be related to the original problem but for what its worth: I installed Cooliris just to check things out. It crashed my Firefox 3.5 and, on some occasions, my PC, every time I used it...

---

