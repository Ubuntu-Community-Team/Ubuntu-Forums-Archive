---
title: "image freezes, sound keeps playing"
date: 2009-07-07
forum: General Help
---

### Post by oh my on 2009-07-07
Hi,

I am using an acer travelmate 6492, hardware specs can be found in this sheet: [http://us.acer.com/acer-v2/datasheet.do?LanguageISOCtxParam=en&sp=page17e&ctx2.c2att1=0&CountryISOCtxParam=US&ctx1g.c2att92=145&kcond65e.c2att101=29169&ctx1.att21k=1&CRC=3291878680](http://us.acer.com/acer-v2/datasheet.do?LanguageISOCtxParam=en&sp=page17e&ctx2.c2att1=0&CountryISOCtxParam=US&ctx1g.c2att92=145&kcond65e.c2att101=29169&ctx1.att21k=1&CRC=3291878680)

I upgraded to 4Gb of RAM but am still using a 32bit release of Jaunty. I am currently using the 020630rc6 kernel mostly because of my intel graphics card, but I have had this problem with the "usual 6.28 kernel" as well.

I am currently using kde 4.2.4 from the  [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) repository as display manager.

My problem is the following:

[COLOR=#000000]Sometimes my desktop gets unresponsive and completely freezes, keyboard does not respond to anything (alt+F4,ctrl+alt+f2,ctrl+alt+del, which is enabled) anymore, you can't even get the led for toggling shift to work, but sound is still playing and I can still move the mouse around (but clicking has no effect whatsoever).[/COLOR]

The freezes are not predictable, I haven't had one in a long time, yesterday I had one and 2 in the last 30 minutes. (of course murphy's law applies: once I finished typing this description, everything froze and I could start all over.:roll: )

Most of the time, the programs running are limited to: firefox, thunderbird, kopete konversation, wicd, konsole, amarok, kaffeine or kteatime. I can't say if one of the programs was running before every freeze.

I tried to troubleshoot this a little a couple of month ago, while still on the 6.28 kernel. But I didn't really get far. 
I installed sensors and checked temperatures, they returned  0°C and 14 °C, which I think isn't correct. After the next freeze I did boot the PC into Vista and checked the temperatures with Speedfan, they were around 40°C, which I think is fine. In both cases I only got temperatures for the CPU, so I still think it might be the graphic chip that is overheating. 
The critical temperatur is set to 106°C with sensors, which I suppose is too high, but I don't know how to change that.

I then installed gnome and ran it for a couple of days. The freezes were less frequent but did still happen. 

I also asked a couple of times on the #kubuntu channel, but nobody could help me.

I need this laptop to work, I need it to be stable and I would really hate to have to switch back to Vista because of this. (which is running fine btw, so I don't think it's faulty hardware) So if anyone has an idea what might be causing these troubles I would be more than grateful!!! :)

If you need any further info, please tell me, thanks! :)

regards Kathrin

EDIT: If this has been posted in the wrong section, please move or tell me so and I will repost in the appropriate section.

EDIT: This is starting to get really annoying. I had 5 more freezes yesterday. :(
I ran a test with sensors, it is now listing more temperatures, but for most I don't know what they are and they give back wrong temperatures:
> Adapter: Virtual device
temp1:       +49.0°C  (crit = +107.0°C)
temp2:        +0.0°C  (crit = +106.0°C)
temp3:        +1.0°C  (crit = +106.0°C)
temp4:       +47.0°C  (crit = +106.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +17.0°C  (high = +100.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +0.0°C  (high = +100.0°C, crit = +100.0°C)

Could you suggest another tool, to check the temperatures?

---

### Post by oh my on 2009-07-09
Hi,

I'm sorry to bump this topic, but it has now gotten down to page 40 and isn't being read by anybody anymore.

I did a Xorg -version in case that info is needed:
```

X.Org X Server 1.6.2
Release Date: 2009-7-7
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-24-xen i686 Ubuntu
Current Operating System: Linux pseudomarge 2.6.30-020630rc6-generic #020630rc6 SMP Mon May 18 15:27:04 UTC 2009 i686
Build Date: 08 July 2009  10:43:16PM
xorg-server 2:1.6.2~git20090708+server-1.6-branch.6f1aff5a-0ubuntu0sarvatt~jaunty (buildd@rothera.buildd
```regards oh my

---

### Post by oh my on 2009-07-15
Could anyone please reply, even if you don't have a clue what I'm talkin about.
I'm getting the feeling, that my postings can't be read. :/

thanks

---

### Post by oh my on 2009-07-18
I blacklisted acer_wmi, but the PC still crashed (and removed it from blacklist after the crash)... anyone willing to help me with this? 
I could really need some help on this, even if it is only to exclude some possible sources, it would help as I have no clue what is causing this for now.

---

### Post by Colo2 on 2009-07-18
I had a simular problem on a PC which hated the ubuntu kernal.

Why don't you try Xubuntu or ubuntu?

It would just be interesting to see if this still happens

---

### Post by oh my on 2009-07-18
Hi,

I installed and tried the gnome desktop for a couple of days a few month back, but still got the freezes. Or did you mean to completely uninstall kde before trying  this?

---

### Post by Colo2 on 2009-07-18
In my case, My pc hated gnome, I installed KDE and it worked. I would try Xubuntu in this case, either wipe the HDD and install or use seperate partitions

---

### Post by oh my on 2009-08-08
Ok, I removed kde and tested gnome. I removed gnome and tested kde (and btw it is a royal PAIN to remove gnome, I had to uninstall every fricking package by hand, because apt-get remove ubuntu-desktop only removed 4 packages out of 500 or so it installed.:x I'm never gonna touch gnome again)

Still it kept freezing every now and then. But I don't suppose anyone has got any idea what is going on or any advice that would help.

---

### Post by benerivo on 2009-08-08
It sounds like a xorg failure. Does it also freeze when desktop effects are disabled? I would have suggested upgrading xorg, but you are on a recent version. Have you tried [this ubuntu repository?]("http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html")

---

### Post by oh my on 2009-08-08
Hi,

I'm already using [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main, I have been using it for about 6 month now. But the problem existed before and persisted after the update.

What kind of desktop effects do you mean? I would expect that if a desktop effect was causing this, then I shouldn't have had crashes under gnome or are they using the same libs to interact with X?

What would you desactivate? Stuff like gliding/exploding windows for sure, but also all widgets? What about the screen edges, should I disable them as well?

EDIT is there any way to log an x-failure or to try to debug this?

regards oh my

---

### Post by benerivo on 2009-08-08
By desktop effects i mean turning compiz or the kde effects off completely, as they both take advantage of hardware (although i think the kde effects can run on software only). In kde it is in System Settings > Desktop. There is the /var/log/xorg.log that you can look at, but i don't know much about what that log contains. You may want to run a session using the vesa driver in xorg, which should prove or disprove that it is an intel/xorg problem.

---

### Post by oh my on 2009-08-08
Hi,

ok I'll try to disable the effects.

The xorg.log does not say anything, no error messages or warnings appear before or after the system freezes. I checked it frequently.

Last time I tried to use vesa-driver (by replacing intel with vesa in the xorg.conf, which is, I assume, what you meant?) I only got a black screen after a reboot. I had to log in through commandline and replace the new xorg.conf by the old one, to get things back to working. Does that mean it is an intel/compatability problem?

regards oh my

---

### Post by benerivo on 2009-08-08
I thought that it was an intel/xorg problem as i've seen other threads about screen + keyboard freezes in linux. What do you have in your xorg.conf file? A xorg.conf file is not needed anymore, and linux can run without it. Have you tried no xorg.conf file, or one that just has...```
Section "Device"
        Identifier "Configured Video Device"
        driver "vesa"
EndSection
```

---

### Post by oh my on 2009-08-08
I haven't tried no xorg.conf yet, no. I will try that once my system freezes with all the desktop effects disabled, so I can be sure what is resolving the issue.

This configuration:
> **benerivo said:**
> ```
Section "Device"
        Identifier "Configured Video Device"
        driver "vesa"
EndSection
```

lets me start ubuntu, but the resolution is all wrong, the optics are horribly fuzzy and I think something ate my theme-settings. It's still set to "slim glow" but the theme is clearly the blue default theme from kde and changing the theme does not have any effect.

My current xorg.conf looked like this:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "AccelMethod" "uxa"
        Option          "EXAOptimizeMigration"   "true"
        Option  "MigrationHeuristic"    "greedy"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```The Device entry was modified, when I updated to the new x-server, I added all the lines starting with "option" back then. (But as mentioned before, the problem existed before and after the update)

regards oh my

EDIT: another big difference I just noticed:
If I am using vesa and hit ctrl-alt-esc to restart the x-server I get back to the login-screen and can log myself back in.
But if I am running intel and restart x-server using ctrl-alt-esc, x-server gets killed and I get a command line, I then have to restart kdm manually before getting to the login-screen.

---

### Post by benerivo on 2009-08-08
If your above attempts don't work, you could try these options in xorg.conf...```
Option "AccelMethod" "exa"
 Option "MigrationHeuristic" "greedy"
 Option "ExaNoComposite" "false"
```instead of your current options.

---

### Post by oh my on 2009-08-08
Hi,

Those settings are for the intel driver, no?

> **benerivo said:**
> Option "AccelMethod" "exa"
 Option "MigrationHeuristic" "greedy"
 Option "ExaNoComposite" "false"

Do you think those could remove the freezes?

The intel driver is working fine and really did improve hugely the fluency of the system. The only drawback is that it might be a possible source of the freezes.

I don't know if you saw my edit (you were probably replying), so I'll post it again:
If I am using vesa and hit ctrl-alt-esc to restart the x-server I get back to the login-screen and can log myself back in.
But if I am running intel and restart x-server using ctrl-alt-esc, x-server gets killed and I get a command line, I then have to restart kdm manually before getting to the login-screen.

I'm not really sure what to make of this. There is no error message or anything when I get to the command line, it just sits their waiting for me to do something.

---

### Post by benerivo on 2009-08-08
I know the xorg 'options' i posted above are alternatives to what i think could be causing the freezes (which i think is a xorg/intel problem.

You really don't want to use vesa permanantly as it has poor performance, and although I can't say about the Ctrl+Atl+Esc differences, i would ignore them for now. Just try having no xorg.conf to see if this fixes the freeze, then using vesa in xorg.conf (to isolate intel as being part of the problem or not), then using the alternative xorg.conf "Options" as a possible fix.

---

### Post by oh my on 2009-08-08
Hi,

I'll do that :)

It's gonna be a while, as those freezes keep coming and going, so I don't know for sure when I'll post back.

regards oh my

---

### Post by oh my on 2009-08-10
Hi,

just to keep you up to date:
I've had no xorg.conf for a day now, whenever I use one of the 3D-effects (eg switching through opened windows) for the desktop, my image completely froze, while sound kept playing.

I was able to use these effects with intel, so I'm gonna try the modified entries for intel you proposed now.

EDIT: 
Ok, let's hope that this is only a temporary problem. Right now every desktop effect leads to a complete freeze of the system, independent of which xorg.conf I use, except for the xorg.conf with vesa, which simply ignores all user settings and leaves all desktop effects disabled and uses all default settings for themes etc.
This is a huge aggravation compared to the situation yesterday. :( I have no idea what might have caused this, I haven't changed any settings, but did install updates yesterday. I think some of them were for the x-server... (is there a way to check what updates I installed on a certain day?)

regards oh my

---

### Post by oh my on 2009-08-10
And now it just froze with the intel-xorg.conf and all desktop effects disabled. :(

---

### Post by oh my on 2009-08-12
I have switched back to the old 28-14-kernel for now. The 30 is getting way to unstable for me now. :(
The freezes continue with every desktop effect or every pop-up independent of the driver I enter into xorg.conf

I can't really watch movies now, but at least the PC stays on for a couple of hours without freezing.

---

