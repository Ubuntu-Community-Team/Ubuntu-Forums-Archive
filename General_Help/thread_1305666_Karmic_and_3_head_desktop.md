---
title: "Karmic and 3 head desktop"
date: 2009-10-30
forum: General Help
---

### Post by Olivier Lec on 2009-10-30
Hi Guys,

Ok I have a 3 monitors setup with 2 video cards.
 
I have two screen in twinview and a separate x for the third screen. 

Before upgrading to Karmic everything was fine, now when I maximize a window on the twinview it goes on the two screens. 

any hint/idea how to fix that ?

Thanks

---

### Post by Olivier Lec on 2009-11-01
~BUMP~ I know everyone is probably busy with Karmic problems but if someone can help would be grateful

---

### Post by Olivier Lec on 2009-11-03
~REBUMP~

do someone need my xorg.conf I can pastebin anything you need but a little help on that one would be **really** appreciated.

---

### Post by Olivier Lec on 2009-11-04
my xorg.conf if anyone interested to help me ... 

[http://pastebin.com/m7c8310d3](http://pastebin.com/m7c8310d3)

---

### Post by Olivier Lec on 2009-11-04
I suppose I will have to find the solution on my own ...

---

### Post by slamhound on 2009-11-05
I've got the same problem on my system, so if you figure out how to fix it, please post (and I'll do the same).

---

### Post by JBAlaska on 2009-11-05
Wish I could help, but I have never used 3 monitors. One thing though, If you google 
```
TwinViewXineramaInfoOrder
``` There's a lot of good info that comes up.

Good luck!

---

### Post by slamhound on 2009-11-05
Okay, found a solution. I don't know if it's the only one or the best one, but it worked for me (at least for the last two minutes).  

If you have CompizConfig Settings Manager installed, go to "General Options" and then "Display Settings".

Uncheck "Detect Outputs" and then manually enter the Outputs in the box labelled "Outputs".  For me (with two 1280x1024 monitors) the two entries are:

1280x1024+0+0
1280x1024+1280+0

The dimensions and offset should be the same as they are in nvidia-settings.

Once I restarted X, maximizing windows worked correctly.

EDIT: Just to clarify, I have three monitors (an additional 1280x1024), but CompizSettings deals with one X screen at a time, so the entries above are for the two monitors on the first GPU linked with Twinview; maximizing already worked correctly with the third monitor on the second GPU.

---

### Post by ad_267 on 2009-11-05
Does this happen with both Compiz and Metacity?

---

### Post by Olivier Lec on 2009-11-06
Thanks for this slamhound, I have tried your solution and yes it fixed the problem on my twinview. only problem my third screen had gone black and it not useable anymore. 

the CCSM doesn't seem to deal with the two screen configuration properly, I have also tried to see if I can edit with Gconf edit with no success so far but we are getting closer to a solution:p

> **slamhound said:**
> Okay, found a solution. I don't know if it's the only one or the best one, but it worked for me (at least for the last two minutes).  

If you have CompizConfig Settings Manager installed, go to "General Options" and then "Display Settings".

Uncheck "Detect Outputs" and then manually enter the Outputs in the box labelled "Outputs".  For me (with two 1280x1024 monitors) the two entries are:

1280x1024+0+0
1280x1024+1280+0

The dimensions and offset should be the same as they are in nvidia-settings.

Once I restarted X, maximizing windows worked correctly.

EDIT: Just to clarify, I have three monitors (an additional 1280x1024), but CompizSettings deals with one X screen at a time, so the entries above are for the two monitors on the first GPU linked with Twinview; maximizing already worked correctly with the third monitor on the second GPU.

---

### Post by Olivier Lec on 2009-11-06
Ok I have played with gconftool-2 like suggested [here]("http://bbs.archlinux.org/viewtopic.php?id=78949") and it works, disable unredirect_fullscreen_windows was an important part .... 

Thanks everyone I could mark it has solved and I should say those 3 days without maximize was hard ):P

> **Olivier Lec said:**
> Thanks for this slamhound, I have tried your solution and yes it fixed the problem on my twinview. only problem my third screen had gone black and it not useable anymore. 

the CCSM doesn't seem to deal with the two screen configuration properly, I have also tried to see if I can edit with Gconf edit with no success so far but we are getting closer to a solution:p

---

### Post by slamhound on 2009-11-06
Thanks for that extra bit of info.  Although I didn't have the black third monitor issue, I did have a problem that your suggestion fixed.  My third monitor (second GPU) worked fine, but then if I tried to maximize a window on this third monitor, it screwed up the settings on the other two such that maximized windows would again span the two monitors.  Setting up the screen1 configuration file fixed it.

---

### Post by slamhound on 2009-11-06
Though now it seems that the settings don't survive a suspend and resume.  The same problem (windows on Monitors 1 and 2 maximize across both, but only if I try to maximize a window on Monitor 3) occurs after resume, but not after reboot or restart of X.  Strange.

---

### Post by slamhound on 2009-11-07
Ugh, spoke too soon, as this is not caused by suspend.  It turns out that although this works at first, for some reason compiz eventually crashes.  For instance, everything usually works fine after reboot or restart of X.  However, after a while, if I try to maximize a window on screen 1 (monitor 3), then it crashes compiz (which then leads to the maximization problem on screen 0 (monitors 1 and 2).  I then have to re-enable effects.

It turns out not to be a huge deal.  Unmaximized Windows on Screen 1 usually pop up at just about full-screen size, so there is no real need to maximize.  And maximization works on Screen 0.  But I might start a new thread to see whether I can get some input on the new specific problem that I'm having.

---

### Post by slamhound on 2009-11-07
Alright, perhaps a fix (though I'll wait and see whether it breaks again).  After resetting everything to the defaults in CompizConfig Setting Manager, I noticed that CCSM reported different values depending on whether I opened it from screen 0 or screen 1 (even though there is a pull down menu from within CCSM to indicate whether the settings are for screen 0 or screen 1--it doesn't seem to work).  So I opened CCSM from the panel in screen 0 and set everything up for the two twinview monitors (the important ones being "do not detect outputs" and setting output to be "1280x1024+0+0 and 1280x1024+1024+0").  Then I opened CCSM from the panel in screen 1 and set the settings for screen 1 (again, "do not detect outputs" and setting the correct output values for the one monitor).  Now maximizing windows in screen 1 does not break the maximizing of windows in screen 0 (or shut down compiz).  We'll see if it lasts.

---

### Post by slamhound on 2009-11-07
Nope that didn't work.  This time it lasted until I logged out of X and then logged back in.  Then, once again, same symptoms came back.

---

### Post by smileypaul on 2009-12-10
Slamhound, thanks for this post.

I have a similar setup with 3 monitors and 2 NVIdia cards.

I had everything working nicely in 8.10.. and it has since gone all downhill for me. 

I'll have some more questions for you in a few days.

---

### Post by slamhound on 2009-12-10
Seems to be working for me now.  As I documented on another thread, the problem seems to be Wobbly Windows.  Once I disabled that, all the other steps that I took worked.  Compiz doesn't crash and windows maximize correctly now.  At least one other poster had the same problem, but it doesn't seem to be universal.  So if Compiz crashes for you, that's one thing to try.

---

### Post by AlexanderDGreat on 2010-03-22
Thanks for figuring this out for all of us! I'm planning to setup 2 vid cards, 3 monitors in Ubuntu myself but, it's gonna be a battle I believe.

---

