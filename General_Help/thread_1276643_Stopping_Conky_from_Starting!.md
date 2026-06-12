---
title: "Stopping Conky from Starting!"
date: 2009-09-27
forum: General Help
---

### Post by Bruce M. on 2009-09-27
**[COLOR="Blue"]Xubuntu 9.04[/COLOR]**

OK, I've got a problem that has been haunting me forever it seems, well since I tested this:

[http://ubuntuforums.org/showpost.php?p=6487829&postcount=5248](http://ubuntuforums.org/showpost.php?p=6487829&postcount=5248)

Of course I will NOT recommend this to anyone!

I tested that with my ~/Conky/conkymain adding the first line to the top and then:

```
chmod +x conkymain
```

It made it executable alright with a side affect, it loads it automatically on boot!  I have NO script to start conky on boot! I have disabled it until I get this fixed.

I changed the "executable" flag so it wasn't executable, by renaming it conkymain.sh and unchecking the executable box under permissions in Thunar, and then renaming it conkymain.  But conkymain keeps coming up on boot.

I changed the name "c-main" it still autoloads.

Today I changed ~/Conky to ~/Conk and what do I see?  The default conky! :confused:

Can anyone tell me how to stop this from happening?

Thanks in advance.
Bruce

PS: Just so you know, I do have my ssc.sh script with an icon on the panel that:
[LIST]
[*]1st click - kills all conkys
[*]2nd click - starts my 4 conkys (one of which is c-main)
[/LIST]

---

### Post by running_rabbit07 on 2009-09-27
Go synaptic and uninstall conky?

---

### Post by VCoolio on 2009-09-27
I'd say it's not so much a conky problem as a wm problem. Did you at some point use a 'remember running apps' feature on shutdown? Does xubuntu have something like that? Anyway, try to restart using that feature with no apps running to remember, especially no conky, then disable the feature again. Just a guess, but it's simple and won't harm anything.

---

### Post by running_rabbit07 on 2009-09-27
> **VCoolio said:**
> I'd say it's not so much a conky problem as a wm problem. Did you at some point use a 'remember running apps' feature on shutdown? Does xubuntu have something like that? Anyway, try to restart using that feature with no apps running to remember, especially no conky, then disable the feature again. Just a guess, but it's simple and won't harm anything.

I have Xubuntu in a VBox and it offers to save running programs for restart. So, yeah, that could be an issue.

---

### Post by mobilediesel on 2009-09-28
As mentioned twice: probably when the window manager is saving the session when it exits. I have Xubuntu 8.04 and was wondering when I first installed it why it was starting stuff up without me telling it to!

Try going to the Settings Manager, into **Sessions and Startup** see if **Automatically save session on logout** is checked. If it is, log out with no programs running. When you log back in, nothing should start unless it's in the **Autostarted apps**. If that worked, go back to the **Sessions and Startup** again and un-check **Automatically save session on logout**.

---

### Post by Bruce M. on 2009-09-28
> **running_rabbit07 said:**
> Go synaptic and uninstall conky?

Funny, I want conky  :)

---

### Post by wojox on 2009-09-28
Remove:

```
#!/usr/bin/conky -c
```

That tells conky to start.

---

### Post by Bruce M. on 2009-09-28
> **wojox said:**
> Remove:

```
#!/usr/bin/conky -c
```

That tells conky to start.

That has been gone for a looooooog time.  :)

---

### Post by wojox on 2009-09-28
Does it always start that same exact script from the photo?

---

### Post by Bruce M. on 2009-09-28
> **VCoolio said:**
> Just a guess, but it's simple and won't harm anything.

> **running_rabbit07 said:**
> I have Xubuntu in a VBox and it offers to save running programs for restart. So, yeah, that could be an issue.

> **mobilediesel said:**
> Try going to the Settings Manager, into **Sessions and Startup** see if **Automatically save session on logout** is checked. If it is, log out with no programs running. When you log back in, nothing should start unless it's in the **Autostarted apps**. If that worked, go back to the **Sessions and Startup** again and un-check **Automatically save session on logout**.

OK, so I unchecked "Save session on logout" and did a restart - conky was still there. checked the "Save session on logout" box and sure enough, it was checked, UNCHECKED it a second time and repeated the process.

This time I got a box asking what session I wanted!
Three options 
1 [a blank space to type something - new session name]
2 [OK] [Cancel]

or similar.
So I typed in bruloo & OK

Now I have an extra step when to loggind in.
A popup screen asking what session I want:

Default - which starts conky, or
bruloo - which does NOT start conky.

I'd rather have the conky starting up at least ssc.sh deletes it and starts my 4 conkys.

problems, problems, problems.

I've only rebooted 6 times this morning after reading all this.  :(

Any suggestion of how to get to ONE session - bruloo as my default?

Have a nice day
Bruce

---

### Post by mobilediesel on 2009-09-28
> **Bruce M. said:**
> OK, so I unchecked "Save session on logout" and did a restart - conky was still there. checked the "Save session on logout" box and sure enough, it was checked, UNCHECKED it a second time and repeated the process.

This time I got a box asking what session I wanted!
Three options 
1 [a blank space to type something - new session name]
2 [OK] [Cancel]

or similar.
So I typed in bruloo & OK

Now I have an extra step when to loggind in.
A popup screen asking what session I want:

Default - which starts conky, or
bruloo - which does NOT start conky.

I'd rather have the conky starting up at least ssc.sh deletes it and starts my 4 conkys.

problems, problems, problems.

I've only rebooted 6 times this morning after reading all this.  :(

Any suggestion of how to get to ONE session - bruloo as my default?

Have a nice day
Bruce

This'll probably take another reboot or two..
Log in with the Default session that currently loads conky,
Check "Save session on logout" and exit after making sure conky is stopped.
If you log back in and conky doesn't start, uncheck "Save session on logout" and you should be set. If conky is running again after that.. well hopefully it wont be! :D

---

### Post by Bruce M. on 2009-09-28
> **mobilediesel said:**
> This'll probably take another reboot or two..
Log in with the Default session that currently loads conky,
Check "Save session on logout" and exit after making sure conky is stopped.
If you log back in and conky doesn't start, uncheck "Save session on logout" and you should be set. If conky is running again after that.. well hopefully it wont be! :D

OK, that "might" clean up "Default" but - it will not get rid of the second "step" upon booting now - that asks "which" session I want to run: Default or bruloo.

In 2006 when things were easier and Xorg didn't "automatically take over your computer" one could simply edit:

```
~/.config/xfce4-session/xfce4-session.rc
```

It doesn't exist today (Xubu 9.04)  :(

---

### Post by Bruce M. on 2009-09-28
{scene: Truckstop on Route 66}
Hey you, Fred, give that truck an extra 200 gallons of diesel on me will ya.
-----------------
> **mobilediesel said:**
> This'll probably take another reboot or two..
Log in with the Default session that currently loads conky,
Check "Save session on logout" and exit after making sure conky is stopped.
If you log back in and conky doesn't start, uncheck "Save session on logout" and you should be set. If conky is running again after that.. well hopefully it wont be! :D

It took 2 - one because I missed something.

I can be soooooo AHHHHHH!!! at times.  Take a look {blushing} at where my mouse is pointing.  {mumble mumble stupid mumble mumble}

**NOW** I can add *ssc.sh* to my Autostart Apps Section  :)

Catch ya on the flipside.
CHIMO!
Bruce

---

### Post by mobilediesel on 2009-09-28
> **Bruce M. said:**
> {scene: Truckstop on Route 66}
Hey you, Fred, give that truck an extra 200 gallons of diesel on me will ya.
-----------------


It took 2 - one because I missed something.

I can be soooooo AHHHHHH!!! at times.  Take a look {blushing} at where my mouse is pointing.  {mumble mumble stupid mumble mumble}

**NOW** I can add *ssc.sh* to my Autostart Apps Section  :)

Catch ya on the flipside.
CHIMO!
Bruce

HA! I *JUST* clicked to reply about **Display chooser on login** when I noticed you replied again!
I saw that in my settings and said to myself "Hey, what's this? I wonder if Bruce saw that.." You must have seen it seconds before I did! :D

---

### Post by Bruce M. on 2009-09-28
> **mobilediesel said:**
> HA! I *JUST* clicked to reply about **Display chooser on login** when I noticed you replied again!
I saw that in my settings and said to myself "Hey, what's this? I wonder if Bruce saw that.." You must have seen it seconds before I did! :D

Well, it's NOT done.

I now have 2 sessions for Ubuntu:
[LIST=1]
[*]Default
[*]bruloo
[/LIST]

And this happens in ***either of those sessions*** (I've rebooted my machine every 3-5 minutes for the last hour)

[LIST=1]
[*]With NO conky running I check Save Session and reboot into the same session.
[*]GREAT - no conky.
[*]reboot just to be sure - no conky.
[*]Add "ssc.sh" to start conky on boot
[*]Check Save Session (since there is no conky) and reboot.
[*]4 conkys come up on boot.
[*]Reboot (using the [X] Save session default)
[*]4 conkys start to come and - blink - gone they're gone and in it comes, my conkymain.  AHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH!!!!!!!!!
[/LIST]

There has to be a way to STOP this from happening!
{grumble grumble $!&%¡#?#¿% grumble grumble}

---

### Post by mobilediesel on 2009-09-28
> **Bruce M. said:**
> Well, it's NOT done.

I now have 2 sessions for Ubuntu:
[LIST=1]
[*]Default
[*]bruloo
[/LIST]

And this happens in ***either of those sessions*** (I've rebooted my machine every 3-5 minutes for the last hour)

[LIST=1]
[*]With NO conky running I check Save Session and reboot into the same session.
[*]GREAT - no conky.
[*]reboot just to be sure - no conky.
[*]Add "ssc.sh" to start conky on boot
[*]Check Save Session (since there is no conky) and reboot.
[*]4 conkys come up on boot.
[*]Reboot (using the [X] Save session default)
[*]4 conkys start to come and - blink - gone they're gone and in it comes, my conkymain.  AHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH!!!!!!!!!
[/LIST]

There has to be a way to STOP this from happening!
{grumble grumble $!&%¡#?#¿% grumble grumble}

I hopefully have found the answer:
from [http://wiki.xfce.org/faq#session_manager](http://wiki.xfce.org/faq#session_manager)
[quote=Xfce wiki]Most of the time closing all the applications and save your session when you logout is sufficient. If this doesn't work, remove the content of the ~/.cache/sessions/ directory when you're not logged in.[/quote]
I'm guessing that you uncheck the Save Sessions, reboot into the liveCD to remove the contents of ~/.cache/sessions/
Then reboot and log in normally.

If THAT doesn't do it :confused:

---

### Post by Bruce M. on 2009-09-29
> **wojox said:**
> Does it always start that same exact script from the photo?

Only when it cannot find "conkymain" or what ever I have renamed conky main to - or where ever I move the file to.

I have:

[LIST=1]
[*]Re-installed Xubu various times and it happens again
[*]Installed newer versions of Xubu and it happens again
[*]Changed ~/Conky/conkymain to ~/Conky/c-main
[*]Changed ~/Conky/c-main to ~/conky/c-main
[*]Changed ~/conky/c-main to ~/conk/c-main
[*]Changed ~/conk/c-main to ~/conk/my-main
[/LIST]

and the very first time I run that file, it always happens after that. :confused:

---

