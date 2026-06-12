---
title: "Removing the sidebar in 11.10 using unity?"
date: 2011-12-04
forum: General Help
---

### Post by christoi28 on 2011-12-04
Hello,
I've been using Ubuntu 11.10 for the past week now and I'm liking it so far. However, I find the sidebar annoying at times (pops up often when I try to go to the previous page on firefox), plus rather useless as I use Gnome Pie. I was looking into a way to remove it.

Taking a quick search, I've found that the common solution is to use something else such as Gnome Classic or KDE. However, there are several features of Unity that I would like to keep, such as the workspace switcher, along with way maximized windows take up the majority of the space. I've looked into other ones like KDE, but really didn't appeal to me as much.

So may question is, are there any programs or anything that can remove the sidebar in Ubuntu 11.10?

---

### Post by hansdown on 2011-12-04
Welcome to the forum,christoi28.

You can move the launcher to the bottom, if you wish.

[http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)

---

### Post by Larkspur on 2011-12-04
Or you could download Compiz Config Settings Manager from the Software Centre, and set the Reveal Edge (in the Unity plugin) to TopLeft.  After doing that, you bring out the launcher bar by moving your mouse to the top-left corner and bringing it down in a straight line (it's easier to do than explain, and becomes a reflex after a couple of times).  That way, you avoid accidentally bringing it out.

---

### Post by oldtimer7777 on 2011-12-04
> **hansdown said:**
> Welcome to the forum,christoi28.

You can move the launcher to the bottom, if you wish.

[http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)

You can move the launcher to the right.  

Or you can move it to the top. 

You can put it right in the middle of screen where it can be even more annoying. 

No, just stick with Fallback Gnome Classic like the rest of us have accept for now.  :)

---

### Post by christoi28 on 2011-12-05
Sorry for the late response. I'll definitely look into both programs, it seems to be exactly what I am looking for. Thank you!!

---

### Post by yetiman64 on 2011-12-05
> **oldtimer7777 said:**
> You can move the launcher to the right.  

Or you can move it to the top. 

You can put it right in the middle of screen where it can be even more annoying. 

Nope, only on the left or on the bottom for the sidebar.

If you are referring to the "reveal mode" function of the "Ubuntu Unity Plugin" then that function can be located anywhere on the screen edge.

> **oldtimer7777 said:**
> No, just stick with Fallback Gnome Classic like the rest of us have accept for now.  :)

:confused: -- see attachments for why you don't have to stick with "Classic". **Just takes some experimenting and knowledge of how to recover a frozen unity plugin. **

Having AWN dock installed makes life much easier to fix things when they lock up (usually only during setting up), particularly if you use the AWN dock "simple launcher" with a custom launcher for the command ```
unity --replace
``` 8th AWN icon from bottom in the 2nd desktop screenshot attached. 

**Note: don't confuse this command with** ```
unity --reset 
```unless of course things go horribly wrong :).

Note the second shot is a better desktop view (the Unity bar on the bottom is set transparent, but is plainly clear as is the AWN dock).

I'm using the Oneiric ppa for the "Ubuntu Unity Plugin Rotated" compiz plugin from the webupd8 page [[COLOR=Blue]--here--[/COLOR]]("http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html"). (this link is taken from the bottom of the page handsdown linked to).

Not sure of your experience level OP, **so take care if you do follow either of the links**.

---

### Post by hansdown on 2011-12-05
That looks pretty nice,yetiman64.

---

### Post by yetiman64 on 2011-12-05
> **hansdown said:**
> That looks pretty nice,yetiman64.
Thanks. Moving the sidebar has made the world of difference for me in Unity with regard to usability.

The cube and expo wall alterations etc are not to be recommended for anyone lacking in experience with compiz. Definitely worth the effort though and has worked wonderfully here. Very happy to use Unity now :D. Cheers.

---

### Post by oldtimer7777 on 2011-12-05
> **yetiman64 said:**
> Nope, only on the left or on the bottom for the sidebar.

If you are referring to the "reveal mode" function of the "Ubuntu Unity Plugin" then that function can be located anywhere on the screen edge.



:confused: -- see attachments for why you don't have to stick with "Classic". **Just takes some experimenting and knowledge of how to recover a frozen unity plugin. **

Having AWN dock installed makes life much easier to fix things when they lock up (usually only during setting up), particularly if you use the AWN dock "simple launcher" with a custom launcher for the command ```
unity --replace
``` 8th AWN icon from bottom in the 2nd desktop screenshot attached. 

**Note: don't confuse this command with** ```
unity --reset 
```unless of course things go horribly wrong :).

Note the second shot is a better desktop view (the Unity bar on the bottom is set transparent, but is plainly clear as is the AWN dock).

I'm using the Oneiric ppa for the "Ubuntu Unity Plugin Rotated" compiz plugin from the webupd8 page [[COLOR=Blue]--here--[/COLOR]]("http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html"). (this link is taken from the bottom of the page handsdown linked to).

Not sure of your experience level OP, **so take care if you do follow either of the links**.

Is there anyway to make the top task bar transparent, so you don't have to have this black bar running along the top of the screen?

---

### Post by larrypg on 2011-12-05
Hello all,

I am not sure this is actually the right place to post this because it seems that a lot of people already do not like the placement of the side launcher.  What I really would like is an explanation of why those who think that it is the best placement for it (on the side).

Some say that it is the most logical place for a large screen but not so good for a smaller screen.  Some mention that the natural flow in the english language is left to right.  Others have said that one should always have it showing and it should not auto-hide.

I have had at least a 19 in monitor since the first day of XP.  My current monitor is 24 inch.  To those who say that it is the most intuitive for it to be on the left...

Just as an example...If I am using FF to browse things...I move my mouse down to the bottom of the screen to get it out of the way.  If I wanted to open another program and my mouse was already on the bottom (or close to it) of the screen it would entail almost no mouse movement to open another program if the launcher was down there.  If it was on the left I would have to move it all the way across the screen to the left. 

To be honest I could care less where it is as I do not use it but to only open another program which I do not do every 5 seconds.  

Like I said I am just interested in the response of those who say it is the best possible placement for the launcher to be on the left and why they think that.  By the way I am not trying to change any opinions or have anyone agree with my own but would like to know.

---

### Post by yetiman64 on 2011-12-05
Topic is drifting a bit, my response to oldtimer7777 is in a PM. Cheers all.

---

