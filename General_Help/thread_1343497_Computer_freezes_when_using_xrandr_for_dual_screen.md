---
title: "Computer freezes when using xrandr for dual screen"
date: 2009-12-01
forum: General Help
---

### Post by drewsus on 2009-12-01
[*[SIZE="1"](I posted this as an addition to another problem I was having, but felt that I should post this as a seperate topic)[/SIZE]*]("http://ubuntuforums.org/showthread.php?t=1343062")

My computer: Acer Aspire One (1gb RAM)
My girl friends: Dell Mini 10v (2gb RAM)

When using xrandr to set up a dual screen environment, her computer is freezing lots That is, it is freezing on the call to xrandr. Additionally, its not just a black screen, the mouse is unmovable and Alt+Sys+R +E +I +S +U +B does not work. A hard shutdown is required

I put it in a script, but just for her convenience. The one to turn it on has one line and is:

```
xrandr --output VGA1 --mode 1440x900 --pos 0x0 --output LVDS1 --mode 1024x600 --pos 0x899
```

The one to turn it off the external is:

```
xrandr --output VGA1 --off --output LVDS1 --mode 1024x600
```

On my computer, I can switch back and forth between them quite rapidly with no problems. I can even set it to start up and if no external monitor is connected it just defaults to the LVDS setting. But on hers, just doing one at any given time can freeze it and it freezes on start up, monitor attached or not.

The Acer Aspire One and Dell Mini 10v have many similarities in hardware (ours both have the Atom n270, GMA 950) but she has 2gb of RAM and I have just 1gb. 

It seems to be much more reliable (FOR HER) when compiz is off (and I stress, it is always on for me when I do it, and I have no problems). 

WHY would hers be freezing so much and causing the problems in the first post?  I told her that maybe her RAM is corrupt. Is this a possible cause for all her problems? 

Please someone help!
Drew

ps- if these problems keep up I am sure I will have no choice but to revert her to Windows (XP or 7 or whatever). But, if its RAM then it might not matter either way.

---

### Post by d1ma5 on 2010-02-23
Hey,

I'm having a similar problem. If I plug in the projector and run ```
xrandr -q
``` or ```
xrandr --output VGA1 --mode 800x600 --pos 0x0
``` or just start the ```
gnome-display-properties
``` my screen freezes and the mouse doesn't move and keyboard doesn't respond to anything and I have to do a hard poweroff. 

If I try to boot with the projector connected I get a kernel panic. My screen also freezes when logging in with the projector connected. I've disabled compiz and even tried it from fluxbox with the same results.

My graphics card is an Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03).

Any help?
~Dimas~

---

### Post by drewsus on 2010-02-23
I discovered that for my ex's monitor, it wasnt properly supported in Ubuntu. Not all the settings were showing in xrandr -q

I wrote a long ~500 line script for doing various things for her dualhead set up. Not getting too into it, I had to add the desired resolution modes to X on start up and then go from there. 

Can you tell me what projector you have? 
Do you know all the resolutions that are supposed to be available for your projector and the desired one you want? 

I may be able to help you with that info.

dRewsus

---

### Post by jwe080 on 2010-03-15
I have exactly the same problem, did either of you resolve this?  Some monitors will work, but projectors don't.

Any help is appreciated.

---

### Post by drewsus on 2010-03-15
answer the same questions from my post above and Im sure I can help....
the more info the better

---

### Post by lavezarez on 2010-03-16
jwe080, d1ma5 - I had the same projector woes like yours and I solved it last night.  I hope these forum links will help you, as it did for me.

1. Check if you have etc\X11\xorg.conf. Go to post # 4 of this [thread]("http://ubuntuforums.org/showthread.php?t=1336863") to help you out if you don't have the file.  Thanks to [Sealbhach]("http://ubuntuforums.org/member.php?u=562588") for this post.
2. Then proceed to follow the step-by-step guide in this [thread]("http://ubuntuforums.org/showthread.php?t=1395876").  Many thanks to [Ares Drake]("http://ubuntuforums.org/member.php?u=139239") for this post.

I didn't exactly follow the guide, though.  Just create 2 scripts - one to enable projector, and another to disable it and restore the original resolution of my notebook.  And I changed the resolutions in the script as Ares used a netbook, having a smaller resolution.

---

### Post by jwe080 on 2010-03-18
Thanks lavezarez those scripts mostly worked, I'll just need to tweak the resolutions as you did.  I think the key was adding the new resolution mode.

I'd just add (for people like me) that the script needs to be run before the projector is plugged in.  Then run
xrandr -q

to check that the resolution of VGA1 is set to the desired resolution (1024x768 worked for me) but is disconnected.  If the resolution isn't there then the projector won't work (or it didn't for me), if it is then try plugging in the projector.

---

