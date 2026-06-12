---
title: "Theme/fonts change on login/startup"
date: 2009-12-01
forum: General Help
---

### Post by drewsus on 2009-12-01
Hello,
So, I have a bit of an odd question.
I installed UNR9.10 on my girlfriends Dell Mini 10v and she has been having problems. Its rather frustrating because I installed it virtually the same way as I did on my Acer Aspire One and I almost never have such problems.

One problem is that when she logs in, her themes and settings seem to revert to something different. 
For instance, I installed the Dust them with Eikon icons. Same on both computers. I also disabled the startup/login sounds. 
But now, SOMETIMES, when she starts up the fonts, icons (normally there is a colourful icon in the top left corner for the main menu applet, but it is back to the ubuntu one when this happens), etc are different and she says that sounds are also enabled (and more so than usual). 
This just started happening randomly, like a week or two after doing a fresh install on her system. 
And, sometimes she logs in and everything is normal.
Also, when everything is different than it should be, opening Appearance settings freezes the computer. And changing the wallpaper has frozen her computer before as well.  
What makes it more difficult is that we are both in separate (but close) universities but its exam time so we cant do too much visiting. Also, shes getting a little sick of things going wonky. Its annoying because I dont ever seem to get as many issues with ubuntu as she does, and I know she isnt messing around with things. Shes not a power user or anything. 

ANY sort of insight would be GREATLY appreciated!!

Thanks in advance, 
dRewsus

---

### Post by drewsus on 2009-12-01
Also, when using xrandr to set up a dual screen environment, her computer is freezing lots (edit: I should say, it is freezing on the call to xrandr. Additionally, its not just a black screen, the mouse is unmovable and Alt+Sys+R +E +I +S +U +B does not work. A hard shutdown is required) 

I put it in a script, but just for her convenience. The one to turn it on has one line and is:

```
xrandr --output VGA1 --mode 1440x900 --pos 0x0 --output LVDS1 --mode 1024x600 --pos 0x899
```

The one to turn it off the external is:

```
xrandr --output VGA1 --off --output LVDS1 --mode 1024x600
```

On my computer, I can switch back and forth between them quite rapidly. But on hers, just doing one at any given time can freeze it.

The Acer Aspire One and Dell Mini 10v have many similarities in hardware (ours both have the Atom n270, GMA 950) but she has 2gb of RAM and I have just 1gb. 

WHY would hers be freezing so much and causing the problems in the first post?  I told her that maybe her RAM is corrupt. Is this a possible cause for all her problems? 

Please someone help!
Drew

ps- if these problems keep up I am sure I will have no choice but to revert her to Windows (XP or 7 or whatever). But, if its RAM then it might not matter either way.

---

### Post by n.hinton on 2010-06-25
Have started getting the same intermittent problem in Lucid as you describe in post #1, although Appearance settings and changing the wallpaper still work fine.

Logging out and back in correct the problem, its just during the full boot it occurs. Also I know when its going to happen, the boot up takes longer and there is more off and on visibility of the mouse pointer during final stages of boot.

Have been trying to trace what causes the issue, but so far unsuccessfully. If anyone can point me in the right direction, I would be most grateful.

---

