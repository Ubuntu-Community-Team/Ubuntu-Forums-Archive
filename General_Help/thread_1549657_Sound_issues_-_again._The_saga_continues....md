---
title: "Sound issues - again. The saga continues..."
date: 2010-08-10
forum: General Help
---

### Post by mastablasta on 2010-08-10
[SIZE=3][FONT=Calibri]Sound issues &#8211; again[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I thought this was a stable system, but i guess i was wrong. It's not even remotely stable on my computer.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]It all started back on December I believe, when new Ubuntu release 9.10 got my attention. I installed it to an old computer. Everything worked fine, but a bit slow. Which was logical since processor was slow by today&#8217;s standards.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I upgraded the system to 10.04 (because I needed newer version of programs) and had flash problems (stuttering). All else worked fine. Since I already planned to upgrade the hardware in July I wasn&#8217;t bothered that much by that. The upgrade came (I made a research on forums to see if planned components would be compatible with Linux and they were).[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Suddenly everything worked fine. But a couple of days later &#8211; disaster &#8211; sound disappeared. I posted about this on forums:[/FONT][/SIZE]
[[FONT=Calibri][SIZE=3][COLOR=#800080]http://ubuntuforums.org/showthread.php?t=1539486[/COLOR][/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1539486")
 
[SIZE=3][FONT=Calibri]Upon several people here and on IRC channels advised ALSA upgrade I did it. I also changed it to use &#8220;analog duplex&#8221;. And the problem was solved. For a few days. Then sound suddenly disappeared again. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Again I sound help on Ubuntu IRC channels and the friendly people there helped me again by telling me how to sort of reload ALSA.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]```
 sudo reload alsa 
```[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]After doing that it worked again. But we came to some conclusion that for some odd reason my sound settings are overwritten or not written down. I also concluded that this happened because of hibernation.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]A few days later sound is off again. This time only in Flash I believe. Computer is restarted things work ok.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]A day later computer freezes on boot. I wasn&#8217;t at home. It&#8217;s actually now my wife&#8217;s computer (uses it to work from home), so she turned it off and on again. System loads properly. All works well. [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Yesterday I turn it on for a quick internet session before bed. System doesn&#8217;t boot. I try recovery mode. Nothing. System just hangs in the middle of the loading (though graphics driver seem to load fine since resolutions changes).[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I try older Kernel system boots fine. Including sound. I go to IRC to seek help yet again. Ubuntu-UK team helps me to read the proper logs (thank you for that). And we identified:[/FONT][/SIZE]
> [FONT=Courier New]There's lots of errors, namely "Aug 9 22:20:47 spodnji-desktop kernel: [ 661.494663] hda-intel: spurious response 0x0:0x0, last cmd=0x970610"[/FONT]
[SIZE=3][FONT=Calibri]I blacklisted the sound module:[/FONT][/SIZE]
[FONT=Courier New]> Add[/FONT]
[FONT=Courier New][/FONT] 
```
[FONT=Courier New]blacklist snd_hda_intel [/FONT]
```
 
[FONT=Courier New]to /etc/modprobe.d/blacklist.conf[/FONT]
 
[SIZE=3][FONT=Calibri]System booted fine with latest kernel. I then commented this line and tried a reboot. Again system booted fine. Sound worked OK. Despite the loading of this module.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Now could someone please tell me what is going on here? And is there a solution to this problem? Should I just format the whole thing and reinstall it? Would that help or just waste my time?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]How can sound work once and then not work the next time?[/FONT][/SIZE]

---

### Post by Jazzy_Jeff on 2010-08-10
I find that upgrades have more problems than doing a clean install. I only do clean installs now and I have had absolutely no problems at all on my desktop, laptop and my sisters desktop. Every thing just works.

---

### Post by mastablasta on 2010-08-10
heh it all just worked here for about a week or more after hardware upgrade. Before upgrade didn't provide any issues (but it was done still with the old mobo).

---

### Post by Jazzy_Jeff on 2010-08-10
I understand that. I have been using 10.04 since release with no issues on the 3 systems. I have always had issues with upgrades in the past and found it was a lot faster for me just to make sure everything was backed up and then the clean install.

---

### Post by mastablasta on 2010-08-10
i doubt this (reinstalling) will help:
[http://ubuntuforums.org/showthread.php?t=1335783](http://ubuntuforums.org/showthread.php?t=1335783)
[http://forums.linuxmint.com/viewtopic.php?f=49&t=44533&start=0](http://forums.linuxmint.com/viewtopic.php?f=49&t=44533&start=0)

there are also bug reports on launchpad, but clearly no one knows the fix.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699)

---

### Post by Riffer on 2010-08-10
Man oh man I feel for you, you've tried everything and now you find that right now theres no fix.  I've googled and it seems that some other distros have the same problem with this chipset.  All I can think of at this point is that you could:

1:  Try another distro, perhaps debian or mint.  As you pointed out in mint it worked.  I know I would be pissed to if I had to change distros just to get sound working.  You could try:

2:  A sound card.  A reasonable card isn't to expensive and I would think that you could turn off the sound module on you MB, so probably your issues would go away.  I have used this solution in the past, both for Linux and Windows.

---

### Post by mastablasta on 2010-08-11
Yesterday i turned computer on. everything worked ok. Did the updates, restarted. everything worked. had to turn it off again (was doing something on electrical grid). turned it back on and everything worked. i checked the logs. now if i understand these logs (system.log) are always created fresh. and this error was still there. so i am worried it's just a matter of time.
 
I am not sure yet but i might be able to salvage a very old sounblaster card. i think (hope) that one should work.
 
But just in case i can not get it, what kind of sound card would be compatible with Linux? I found a cheap Genious card (Genius SoundMaker Value 5.1, PCI), but upon searchign the net there were some issues reported even on this forum.
 
The thing is my funds are limited and even more importantly i don't need some high quality surround sound actually. Just two speakers to listen (actually my wife will listen) to occasional movie, little a bit of music and a certain "alarm" plugin.

---

### Post by Riffer on 2010-08-11
> **mastablasta said:**
> I am not sure yet but i might be able to salvage a very old sounblaster card. i think (hope) that one should work.
 
But just in case i can not get it, what kind of sound card would be compatible with Linux? I found a cheap Genious card (Genius SoundMaker Value 5.1, PCI), but upon searchign the net there were some issues reported even on this forum.


[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards")

Remember some generic cards (sound and video)use chipsets from the big manufacturers.  I have a video card that isn't nVidia but has its chipset and works as a nVidia card. 

Just did a quick search and it seems that there is a ALSA module for that card.

---

