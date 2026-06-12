---
title: "Ubuntu 11.04 Date and calendar is NOT on the top panel"
date: 2011-04-25
forum: General Help
---

### Post by Kate the Enthusiast on 2011-04-25
Suddenly the date and time applet disappeared from my top panel.
I have checked out Compiz Setting Manager and asked google but without success. 

Does anybody know how to tackle this one?

P.S. For those who have not got 11.04 yet: right click on the panel does not give you a choice of applets in 11.04 as it was in 10.10.

---

### Post by pctx on 2011-04-25
Hey Kate,

I've noticed Unity being weird in that regard.  You didn't happen to move it to another panel did you? (I.E. you unlocked it and moved it by accident?) I'm firing up my VM to take a look at how that can be re-added.

-A

---

### Post by Kate the Enthusiast on 2011-04-25
> **pctx said:**
> Hey Kate,

I've noticed Unity being weird in that regard.  You didn't happen to move it to another panel did you? (I.E. you unlocked it and moved it by accident?) I'm firing up my VM to take a look at how that can be re-added.

-A

Hello Pctx, 

I dont have another panel because I have not yet  figured out how to configure another panel in 11.04.

I have this dock thing on the left and the top panel. 

well, the only thing I have done is installing some themes but they are from the standard Art Gnome place,
nothing fancy.

Thank you for trying to help!

---

### Post by pctx on 2011-04-25
One thing to see... Log out and go into "Ubuntu Classic"  and see if your time and date appear.  If it does, then it sounds like it's a shell issue of which at that point, it's probably going to require someone who is more familiar with Unity that myself.

If it does not show up, try right clicking and adding the clock applet.  It should pop back up and then log off, go back into Ubuntu "proper" (with Unity) and see if it shows up or if its still gone.

---

### Post by Kate the Enthusiast on 2011-05-01
> **pctx said:**
> One thing to see... Log out and go into "Ubuntu Classic"  and see if your time and date appear.  If it does, then it sounds like it's a shell issue of which at that point, it's probably going to require someone who is more familiar with Unity that myself.

If it does not show up, try right clicking and adding the clock applet.  It should pop back up and then log off, go back into Ubuntu "proper" (with Unity) and see if it shows up or if its still gone.

Nope, Classic does not give me desired clock and calendar.

Right clicking on the panel has gone with ubuntu 10.10 for me :(
Unity imitates Apple I guess so we need this top panel for the menus.

---

### Post by sg1efc on 2011-05-01
> **Kate the Enthusiast said:**
> Nope, Classic does not give me desired clock and calendar.

Right clicking on the panel has gone with ubuntu 10.10 for me :(
Unity imitates Apple I guess so we need this top panel for the menus.

When you are in Classic, did you try right-clicking on the top bar?  Hopefully that will give you a box with options, select "Add To Panel" and then select "Clock".  :)

I did not like the Unity layout, so after about 5 minutes I selected Classic.

---

### Post by Kate the Enthusiast on 2011-05-02
> **sg1efc said:**
> When you are in Classic, did you try right-clicking on the top bar?  Hopefully that will give you a box with options, select "Add To Panel" and then select "Clock".  :)

I did not like the Unity layout, so after about 5 minutes I selected Classic.

He-he, thanks for a lesson. I've decided for some reason that one can switch into the Classic mode by going into compiz-config-settings-manager and disable "unity". Well, the panels have disappeared and did not appeared after restart. Alt+F2 does not work, "create launcher" on the desktop does not work either. I have spend lovely 30 min struggling with ubuntu on my own. But it was fun. :popcorn:

More to the point. I prefer to keep Classic mode as I have been suffering for quite some time with Unity and sort of got used to it. 

Thanks for trying to help me!

---

### Post by Blasphemist on 2011-05-02
Change the theme and see if it reappears. Try a few if you need to. Some themes, and you said you were in that area, cause the date/time to be invisible.

---

### Post by Randicus on 2011-05-02
After reading your post I checked my computer and noticed the date was not displayed, only the time. I am not sure if it is the same with you or if you do not have the time either. The solution was very easy for me. I left-clicked on the time and the calander came up, then clicked "settings." I was given the option of adding the date to the tool bar. I hope this helps you.

---

### Post by uRock on 2011-05-02
> **Randicus said:**
> After reading your post I checked my computer and noticed the date was not displayed, only the time. I am not sure if it is the same with you or if you do not have the time either. The solution was very easy for me. I left-clicked on the time and the calander came up, then clicked "settings." I was given the option of adding the date to the tool bar. I hope this helps you.

I had just found that same info a little while ago. I'll throw in screenshots.

---

### Post by Kate the Enthusiast on 2011-05-02
> **Randicus said:**
> After reading your post I checked my computer and noticed the date was not displayed, only the time.

Hmm.. I have not got even time.  Left clicks on the panel do not help.

Played around with Themes changing them to something more standard. Does not help yet.

Still looking.

---

### Post by Blasphemist on 2011-05-02
Solution yet Kate? I was where you are back in alpha time and had little idea where to go. I don't think my solution was a good one but eventually I got it back. Now I have it working well for me. I can search for the more elegant and appropriate solutions I've seen in here if you tell me where you stand now, or help you get from whatever issue you now have back to where you want it.

---

### Post by naturewise on 2011-05-02
I had exactly the same problem, the clock was gone. But I have to admit, it was my fault, I deinstalled everything related to this envelope on the panel (Gwibber, Evolution, Ubuntu One). And to remove the envelope itself, I removed the package indicator-messages. To remove the panel item with the actual user I removed indicator-me. Well, I apparently removed too much, so the clock was also gone. To get it back, do the following:
1. Go into Synaptic Package Manager
2. Search for "indicator clock"
3. Install indicator-datetime and its dependency

Hope it works for you, too!

---

### Post by foodmonkey on 2011-05-02
terminal aptitude show indicator-datetime
see if the output says it is installed
if it isn't apt-get install indicator-datetime

if it is purge it and reinstall and restart

mine reappeared after this in about 10 minutes or so. going from unity to classic mode seems to cause this.

cheers,
the foodmonkey

---

### Post by Kate the Enthusiast on 2011-05-03
> **naturewise said:**
> I had exactly the same problem, the clock was gone. But I have to admit, it was my fault, I deinstalled everything related to this envelope on the panel (Gwibber, Evolution, Ubuntu One). And to remove the envelope itself, I removed the package indicator-messages. To remove the panel item with the actual user I removed indicator-me. Well, I apparently removed too much, so the clock was also gone. To get it back, do the following:
1. Go into Synaptic Package Manager
2. Search for "indicator clock"
3. Install indicator-datetime and its dependency

Hope it works for you, too!

> **foodmonkey said:**
> terminal aptitude show indicator-datetime
see if the output says it is installed
if it isn't apt-get install indicator-datetime

if it is purge it and reinstall and restart

mine reappeared after this in about 10 minutes or so. going from unity to classic mode seems to cause this.

cheers,
the foodmonkey

Oh, yes, I had also deleted all the gwibber-related things. So I have installed the indicators back and now the date, time and weather are back.

I thank everybody and mark this thread as solved.

---

