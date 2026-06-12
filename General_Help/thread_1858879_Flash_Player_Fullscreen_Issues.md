---
title: "Flash Player Fullscreen Issues"
date: 2011-10-13
forum: General Help
---

### Post by v2580s on 2011-10-13
Hello,
so I have this weird problem that I have noticed it to occur only with gamespot videos...!!!
When I turn the video in fullscreen it doesn't use the whole screen but a part of it. I tried reinstalling flash player plugin but nothing happened. Even though I this problem happens only with gamespot I have also noticed delays with the player controls in other sites.(pressing pause takes a while to  execute)
The problem occurs with all the browsers I've tried and with both KDE and Gnome.

Flash Version: 11.0.1.152
Screen resolution: 1920x1080

Screenshot: Full Screen gamespot video

---

### Post by SeijiSensei on 2011-10-13
What video card do you have?

I picked a Gamespot video at random, and it played correctly in full-screen (1280x720 in my case).  I also played another Gamespot video (the Cars 2 trailer) with native 720p resolution in full-screen without problems.

I'm using Kubuntu 10.10 with an NVIDIA 9500GT video adapter.  I'm also running Flash version 11.0.1.152.

You might want to try running [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

---

### Post by v2580s on 2011-10-14
My video card is Nvidia 8800GTS. The problem occurs no matter the resolution I pick for the video. 
I will try this Flash-aid addon! Thanks!

UPDATE: Tried Flash-Aid nothing changed...

---

### Post by SeijiSensei on 2011-10-14
> **v2580s said:**
> My video card is Nvidia 8800GTS. The problem occurs no matter the resolution I pick for the video.

Are you using the proprietary NVIDIA driver?  If not, run the "Additional Hardware" application to install the driver.  See if that helps.

---

### Post by v2580s on 2011-10-18
The driver is installed and active... Oh well.... It's an annoying problem but not that important. I'll just watch my videos from another site!!!
Thanks for the help!

---

### Post by lovinglinux on 2011-10-18
Are you using a dual monitor setup? These usually happens because one monitor has different resolution and flash detects the lower one.

---

### Post by v2580s on 2011-10-19
Yes dual-monitor...
1920x1200 Primary
1680x1050 Second

So you're saying that by lowering the primary resolution I solve the problem right?
Maybe you have an idea why this happens on gamespot and not youtube for instance?

Thanks!

UPDATE: Unfortunately that didn't solve the problem either... Although the video got a bit bigger... But I cannot turn my monitors to 800x600 resolution... I hear IGN is a good gaming site...

---

### Post by lovinglinux on 2011-10-19
> **v2580s said:**
> Yes dual-monitor...
1920x1200 Primary
1680x1050 Second

So you're saying that by lowering the primary resolution I solve the problem right?
Maybe you have an idea why this happens on gamespot and not youtube for instance?

Thanks!

UPDATE: Unfortunately that didn't solve the problem either... Although the video got a bit bigger... But I cannot turn my monitors to 800x600 resolution... I hear IGN is a good gaming site...

Probably the player used by the site.

Looks like putting the larger screen on the left in the display settings could solve the problem.  

[http://ubuntuforums.org/showthread.php?t=1236791](http://ubuntuforums.org/showthread.php?t=1236791)

If not, then try this:

[http://ubuntuforums.org/showthread.php?t=1829272](http://ubuntuforums.org/showthread.php?t=1829272)

I haven't tested that, but looks like a possible solution.

There are other threads without solution or with suggested workarounds:

[http://ubuntuforums.org/showthread.php?t=1705577](http://ubuntuforums.org/showthread.php?t=1705577)
[http://ubuntuforums.org/showthread.php?t=1009461](http://ubuntuforums.org/showthread.php?t=1009461)

---

### Post by v2580s on 2011-10-20
Unfortunately none of the mentioned threads helped... Tried the script and nothing changed...
The fact that this occurs only with gamespot should mean that there is a problem with the specific player, right? Youtube, vimeo and other video sites that I use work just fine...
Also tried opening firefox with error console and debugging info but nothing helpful came up... (which makes sense since the problem is caused by the flash player and not the browser).

---

### Post by lovinglinux on 2011-10-20
> **v2580s said:**
> Unfortunately none of the mentioned threads helped... Tried the script and nothing changed...
The fact that this occurs only with gamespot should mean that there is a problem with the specific player, right? Youtube, vimeo and other video sites that I use work just fine...
Also tried opening firefox with error console and debugging info but nothing helpful came up... (which makes sense since the problem is caused by the flash player and not the browser).

Yes. If other sites are ok, is probably the player on the page.

---

