---
title: "Fresh 10.04 Boots with Partial Panels"
date: 2010-05-22
forum: General Help
---

### Post by jamesisin on 2010-05-22
When I boot this machine with freshly installed 10.04 I get some of the panels displayed.

I can force Ubuntu to build them correctly by switching themes.  I can then, if desired, switch back.  This is an imperfect workaround and does not always do the trick.  I have tried a few other tricks and nothing seems to work.

Always rebooting returns the problem (regardless of which theme is running at shutdown).

Something seemed to flash once at the blank space to the right where the panels end (along the right edge--a rectangular maybe), but it flashed and I only saw it once, but it would fit that space.

Finally, I can add items to the partial panels and they will not appear until I have run the workaround above.

I need a fix for this as the workaround is itself unreliable and far too much a hassle to use regularly.  Oh, I tried just rebuilding the machine over and came to the same end.

---

### Post by Elfy on 2010-05-22
Have you tried to reset them to default?

I've done this in the past

```
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

---

### Post by jamesisin on 2010-05-22
If I run "rm -rf ~/.gconf/apps/panel" will the system rebuild /panel at some point (reboot?)?

---

### Post by Elfy on 2010-05-22
After killing the panel afterwards - they start again - or at least they did for me. I ahd a bug in jaunty or karmic - I was constantly needing to do it if I forgot not to do the thing that caused the bug.

If you are not sure about running the rm command move the panel folder out of .gconf/apps to the desktop or something.

---

### Post by jamesisin on 2010-05-22
Running those commands did reset the panels in the same manner that changing the theme would have.  However, upon reboot I am back with this problem.

---

### Post by jamesisin on 2010-05-22
Any other suggestions out there?

---

### Post by jamesisin on 2010-05-22
Anybody?

---

### Post by jamesisin on 2010-05-22
Please?

---

### Post by mikewhatever on 2010-05-22
> **jamesisin said:**
> Running those commands did reset the panels in the same manner that changing the theme would have.  However, upon reboot I am back with this problem.

If changing the theme fixes it, just use a different theme.

---

### Post by jamesisin on 2010-05-22
> **mikewhatever said:**
> If changing the theme fixes it, just use a different theme.

> **jamesisin said:**
> I can force Ubuntu to build them correctly by switching themes.  I can then, if desired, switch back.  This is an imperfect workaround and **does not always do the trick**.  I have tried a few other tricks and nothing seems to work.

**Always rebooting returns the problem** (regardless of which theme is running at shutdown).

[Emphasis added.]

Besides, I shouldn't have to write some script to change the theme (and then change it back) at boot time every time.  That's just silly.  I should fix the problem.  I just don't know what the problem really is.

---

### Post by jamesisin on 2010-05-22
Seriously?  No love?

---

### Post by Elfy on 2010-05-23
If it is just one theme and it's a default one - try a bug report.

---

### Post by jamesisin on 2010-05-23
It is not theme dependent.  It happens no matter which theme (among the defaults mind you) I choose.

I could still file a bug report, but I don't really know what I'm going to say (other than perhaps echoing my post here).

---

### Post by Elfy on 2010-05-23
The only other thing I would try would be remove all the gnome configs from home - backing them up as necessary - e-mails/bookmarsk etc - whatever that is there in fact.

Logout and back in - then start to move stuff back and see if you can get it that way - sorry I can't be of more help.

I know that if you're not sure what to put the bug against then ubuntu-bug gives you same basic choices - other would be my choice then when it get's triaged they'd put it where it was needed.

Edit - actually using the xorg option in ubuntu-bug gets this new menu to choose from - screenshot

---

### Post by Elfy on 2010-05-23
Would appear that you are not alone - [http://ubuntuforums.org/showthread.php?t=1491135](http://ubuntuforums.org/showthread.php?t=1491135)

---

### Post by artlogic on 2010-05-23
Seeing the same behavior here.  I can start the panel manually, but nothing seems to make it come up on boot.  I'm not near the computer so I can't troubleshoot it.  It's a fresh install with all the updates applied.

I'll post once I can spend some time troubleshooting it.

---

### Post by lone_wolf45 on 2010-05-25
I'm not really sure what the problem is. It happens to me as well, it's definitely not the cd, and ubuntu 9.10 doesn't have the same problem on the same computer, so i can confirm it's 10.04. 
 
For me I dont have to type out 
 
"gconftool --recursive-unset /apps/panel, 
 
then 
 
rm -rf ~/.gconf/apps/panel 
 
and then 
 
pkill gnome-panel"
 
just "pkill gnome-panel" does it and i have to run it every time i start ubuntu 10.04. 
 
I have thought about making this a script that runs every time i boot, but i agree, this is not the answer and we should try to find the problem itself, rather than circumvent around it.

---

### Post by jamesisin on 2010-05-25
I have confirmed that pkill gnome-panel is sufficient to start the panels correctly.

I intend to file a bug report (perhaps later today).  If one of you has already created a bug report, please point me to it.

---

### Post by jamesisin on 2010-05-25
Well, now that I ran pkill gnome-panel by itself I can't get the panels to bork on boot.  If anyone else can boot into borked panels, please follow these procedures to file a bug report:

[https://help.ubuntu.com/community/ReportingBugs#Filing a bug with ubuntu-bug](https://help.ubuntu.com/community/ReportingBugs#Filing a bug with ubuntu-bug)

Then point the report back to this thread for more information (and link this thread to the report.

If it happens again on this system (and it was happening at each and every boot), I'll file one.

---

### Post by jamesisin on 2010-05-25
Looks like this fix functions on a per user basis.  Creating a new user account shows the same behaviour.

I have filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/585659](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/585659)

Contribute if you are able.

---

