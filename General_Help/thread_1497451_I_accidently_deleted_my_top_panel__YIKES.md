---
title: "I accidently deleted my top panel  YIKES"
date: 2010-05-30
forum: General Help
---

### Post by melinda on 2010-05-30
Hi

I accidentally hit the delete this panel when I right clicked on the top.

HOW TO I CREATE A NEW TOP PANEL WITH ALL THE DEFAULTS?

Thanks

Melinda

---

### Post by Swagman on 2010-05-30
Right click on the bottom panel and select "Help"

---

### Post by melinda on 2010-05-30
did that. cant find where it says how to restore the default settings.  I see what some of the default things are.  but now how to restore default (do it looks and has exactly what was on it)

---

### Post by Dave_gb on 2010-05-30
[SIZE=2]Open Terminal: Ctrl+Shift+T[/SIZE]
 [SIZE=2]Execute these three commands:[/SIZE]
 [INDENT][SIZE=3]gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/SIZE]
[/INDENT] [SIZE=2]The panels should reappear without logging out.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Hope it helps a little more than the previous reponse :rolleyes:
[/SIZE]
[SIZE=2]
[/SIZE]

---

### Post by WorMzy on 2010-05-30
"rtfm" or equivalent is not a very helpful response, Swagman, and it's against the code of conduct to suggest it.

Melinda, you can add a new panel by right clicking on the remaining panel and choosing "new panel".

If necessary, you can reposition the new panel by right-clicking it, choosing properties, and changing the orientation.

To add applets to the new panel, right click on the panel and choose "add to panel".

The default top panel has "Menu Bar", "Clock", "Notification Area", "Indicator Applet", and "Indicator Applet Session". Add these by dragging them onto the new panel, and reposition them as you see fit.
Program shortcuts can be re-added by browsing the Applications menu, right clicking on the Application you want on the panel, and choosing "Add this launcher to panel".


If you'd rather just restore the default panels, which will reset any changes you've made to the bottom panel too, then open a terminal (if necessary, you can create a launcher on your desktop which opens "gnome-terminal" for this) and run:
```
mkdir ~/.oldpanel
```then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```then
```
*gconftool-2 --shutdown*
```finally
```
pkill gnome-panel
```

---

### Post by melinda on 2010-05-30
>hope it helps a little more than the previous response<

uhhh......AND HOW!  :P  

DAVE you TOTALLY ROCK!  EXACTLY!  what I was asking for!  

peace!  

Melinda

---

### Post by Swagman on 2010-05-30
> **Dave_gb said:**
> [SIZE=2]Open Terminal: Ctrl+Shift+T[/SIZE]
 [SIZE=2]Execute these three commands:[/SIZE]
 [INDENT][SIZE=3]gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/SIZE]
[/INDENT] [SIZE=2]The panels should reappear without logging out.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Hope it helps a little more than the previous reponse :rolleyes:
[/SIZE]
[SIZE=2]
[/SIZE]

Perhaps because I didn't know that command but I can point her to the help file so she can rebuild a new one huh ?

---

### Post by vaiocomputer on 2010-05-30
Or, alternatively, you could right click the botton panel and select "New Panel". Drag it to the top if it isn't there already and download a full sized image of a default Ubuntu installation from Google Images. 

And you can fiddle around the different things you can add to the panel (right click) to restore the original look.  There are only a few things, so it isn't that hard, and it will get you some increasing familiarity with the different things you can add to your panels.

---

### Post by melinda on 2010-05-30
Have to say...

I did add new panel....added the items one by one...but doesn't look the same:  sound icon diff, evolution icon diff, no help icon, cant add the messenger biz, shutdown icon diff....etc.

So Dave_gb was on the money.  :)

WorMzy was a good response too tho -- however don't get why you say that "rtfm" is against code of conduct?  It worked perfectly.

Thanks All!

Peace!

---

### Post by Swagman on 2010-05-30
> **melinda said:**
> Have to say...

I did add new panel....added the items one by one...but doesn't look the same:  sound icon diff, evolution icon diff, no help icon, cant add the messenger biz, shutdown icon diff....etc.

So Dave_gb was on the money.  :)

WorMzy was a good response too tho -- however don't get why you say that "rtfm" is against code of conduct?  It worked perfectly.

Thanks All!

Peace!

No worries... It's no fun waiting for a response when you need help so even a... "I read your plea" kinda helps.

---

### Post by WorMzy on 2010-05-30
rtfm = read the ****ing manual, it's rude, it's not a very helpful response, and since it makes the topic look more active than it really is, the topic may not get the attention of people who can genuinely help. "Just google it" is also discouraged, for the same reason. :)

---

### Post by Swagman on 2010-05-30
True but I never said RTFM. There is no point me typing out stuff from a help file she already has on her machine so I pointed her precisley to where she can read it herself.

And my post bumped it up the list and made you all look at it.


Job sorted.

---

### Post by VastOne on 2010-05-30
> **WorMzy said:**
> rtfm = read the ****ing manual, it's rude, it's not a very helpful response, and since it makes the topic look more active than it really is, the topic may not get the attention of people who can genuinely help. "Just google it" is also discouraged, for the same reason. :)

Fist off, your help on this and your solutions were incredible///

I am a bit confused tho...I have been pointed to the man pages on several occasions and have found them to be invaluable. They are equivalent to rtfm, but I was not aware of a policy towards encouraging people to read something like the man pages to help them learn. 

If more people understand that they can use google effectively to find their solutions by using variables, the better we would all be.  I cannot tell you how many ppl I have helped here by simply finding the solution in a google search and providing it without having a clue as to what the actual problem was or how to solve it.  

Just saying....

---

### Post by finlost on 2010-05-30
> **VastOne said:**
> If more people understand that they can use google effectively to find their solutions by using variables, the better we would all be.  I cannot tell you how many ppl I have helped here by simply finding the solution in a google search and providing it without having a clue as to what the actual problem was or how to solve it.  

Just saying....
+1

My pet peeve is the repetition of some of the same issues.  The problem in this thread is a classic example. It seems the "I accidentally deleted a the top panel" or "Firefox is slow" can be found on almost every page in the General Help section of this forum.

---

### Post by VastOne on 2010-05-30
> **finlost said:**
> +1

My pet peeve is the repetition of some of the same issues.  The problem in this thread is a classic example. It seems the "I accidentally deleted a the top panel" or "Firefox is slow" can be found on almost every page in the General Help section of this forum.

As an example, this google search variable  - [_[COLOR="Lime"]site:ubuntuforums.org ubuntu restore panel[/COLOR]_]("http://www.google.com/search?hl=en&safe=off&q=+site:ubuntuforums.org+ubuntu+restore+panel&ei=3iADTL_eNoOINsr6gDw&sa=X&oi=forum_cluster&resnum=1&ct=more-results&ved=0CBkQrQIwAA") returned 124,000 hits and the first 3 pages were totally on track....

---

### Post by bcbc on 2010-05-30
> **VastOne said:**
> As an example, this google search variable  - [_[COLOR="Lime"]site:ubuntuforums.org ubuntu restore panel[/COLOR]_]("http://www.google.com/search?hl=en&safe=off&q=+site:ubuntuforums.org+ubuntu+restore+panel&ei=3iADTL_eNoOINsr6gDw&sa=X&oi=forum_cluster&resnum=1&ct=more-results&ved=0CBkQrQIwAA") returned 124,000 hits and the first 3 pages were totally on track....

Which makes you wonder why someone doesn't invent a restore panel feature, or even prevent deleting of the top panel (without sudo intervention and a suitable warning). Or something!

I mean seriously, gconftool-2 --recursive-unset/-shutdown, pkill/killall gnome-panel etc. - that must win the obscure coding award for sure.

---

### Post by finlost on 2010-05-30
> **VastOne said:**
> As an example, this google search variable  - [_[COLOR="Lime"]site:ubuntuforums.org ubuntu restore panel[/COLOR]_]("http://www.google.com/search?hl=en&safe=off&q=+site:ubuntuforums.org+ubuntu+restore+panel&ei=3iADTL_eNoOINsr6gDw&sa=X&oi=forum_cluster&resnum=1&ct=more-results&ved=0CBkQrQIwAA") returned 124,000 hits and the first 3 pages were totally on track....
And [Google Ubuntu]("http://www.googlubuntu.com/")

---

### Post by finlost on 2010-05-30
> **bcbc said:**
> Which makes you wonder why someone doesn't invent a restore panel feature, or even prevent deleting of the top panel (without sudo intervention and a suitable warning). Or something!

I mean seriously, gconftool-2 --recursive-unset/-shutdown, pkill/killall gnome-panel etc. - that must win the obscure coding award for sure.
Does right clicking on the panel and then checking the box "Lock To Panel" prohibit deleting a panel?

---

### Post by ezsit on 2010-05-30
Someone wrote:
> "rtfm" or equivalent is not a very helpful response, Swagman, and it's against the code of conduct to suggest it.

What? Really? Since when is reading and education against the code of conduct? I cannot think of a more unenlightened code of conduct that would require users never to suggest to other users to read the instructions. That is just absurd.

---

### Post by bcbc on 2010-05-31
> **finlost said:**
> Does right clicking on the panel and then checking the box "Lock To Panel" prohibit deleting a panel?

I believe that merely prevents an item on the panel from being moved to another position.

---

### Post by finlost on 2010-05-31
bcbc - I am thinking the same.

---

