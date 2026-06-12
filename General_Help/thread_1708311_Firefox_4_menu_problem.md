---
title: "Firefox 4 menu problem"
date: 2011-03-16
forum: General Help
---

### Post by BobvanderPoel on 2011-03-16
I have firefox 4 (rc1) on my Ubuntu 10.10 running Gnome and Compiz. I'm including these details since I'm not sure where the problem is.

Everything seems to be running just fine and smooth. A few of my old extensions are missing, but that will come with time.

Now, the problem: After a random time (minutes or hours) the menus in the menu bar (File Edit ... Help) stop working. The labels are there, and if I click on a label I get the menu items. However, if I try to click on an item the menu disappears. I can select items via the keyboard.

I can solve the problem simply by minimizing and then, immediately, maximizing the firefox window. Very odd?

So far I've tried the following without success:

  - run firefox in safe mode with extensions disabled. No difference.

 - disabled my unclutter to hide the mouse after a delay. No difference.

I'm thinking that this is not a firefox issue? But, really don't know. 

Any suggestions etc. appreciated.

---

### Post by Lucradia on 2011-03-17
Are you using a 64-bit OS?

---

### Post by BobvanderPoel on 2011-03-17
No 64 bit here. Just plain old 32.

Not that it _should_ matter ... but I'm using an Nvidia gfx card with a 260.19.06 driver.

---

### Post by Lucradia on 2011-03-17
> **BobvanderPoel said:**
> No 64 bit here. Just plain old 32.

Not that it _should_ matter ... but I'm using an Nvidia gfx card with a 260.19.06 driver.

Just needed to know; since GIMP 64-bit will randomly not show menu items after so long of usage.

---

### Post by asmoore82 on 2011-03-17
It sounds like it could be the known bug in Compiz "Desktop Effects."
It's extremely prone to manifest immediately after a laptop resumes.

---

### Post by pqwoerituytrueiwoq on 2011-03-17
heard restarting firefox takes care of it
i typically use arrow keys and enter to bypass it

---

### Post by peculiar penguin on 2011-03-18
What are your screensaver settings? I'm seeing this behaviour after the screen was auto-locked by the screensaver ("Lock screen when screensaver is active") while Firefox was running. Manually locking the screen does not cause it. This isn't new with RC1 either but happened with all betas I used (everything from beta 6 onwards, IIRC).

---

### Post by BobvanderPoel on 2011-03-18
> **peculiar penguin said:**
> What are your screensaver settings? I'm seeing this behaviour after the screen was auto-locked by the screensaver ("Lock screen when screensaver is active") while Firefox was running. Manually locking the screen does not cause it. This isn't new with RC1 either but happened with all betas I used (everything from beta 6 onwards, IIRC).

My screensaver just comes up. No password/locking going on. Just checked after letting FF4 run overnight (with the screensaver on) and it's working fine right now.

All very strange :)

---

### Post by BobvanderPoel on 2011-03-20
I grabbed the new RC2 last night ... figured it might fix my problem :)

Nope. Still losing menus. Oh well. Does anyone know if the the firefox folks are aware of the problem? I've done a search on the mozilla site(s) but didn't find this issue.

---

### Post by SavageWolf on 2011-03-20
I have this problem sometimes, CTRL+ALT+F1 then CTRL+ALT+F7 seems to fix it.

---

### Post by BobvanderPoel on 2011-03-20
> **SavageWolf said:**
> I have this problem sometimes, CTRL+ALT+F1 then CTRL+ALT+F7 seems to fix it.

I'm wondering if this is a Compiz issue? Question: Are all the people having the problem using compiz?

---

### Post by eric1959 on 2011-03-22
> **BobvanderPoel said:**
> I'm wondering if this is a Compiz issue? Question: Are all the people having the problem using compiz?


[http://forums.debian.net/viewtopic.php?f=6&t=61909](http://forums.debian.net/viewtopic.php?f=6&t=61909)

---

### Post by platosearwax on 2011-03-22
I had a similar problem with Firefox where after a going to screensaver and coming back I got no searches when typing in the url bar. I can't find the thread but it seemed like it was a bug in Compiz where the pop down search was being drawn but behind Firefox. Something to do with a window focus bug in Compiz.

I shut my screensaver off and just had the monitor power down after 5 minutes and have not had a problem since.

---

### Post by drammock on 2011-03-24
> **SavageWolf said:**
> I have this problem sometimes, CTRL+ALT+F1 then CTRL+ALT+F7 seems to fix it.

This technique did not fix it for me.  However, minimizing then restoring the firefox window (as suggested in the debian forum thread linked by eric1959 does (temporarily) fix the problem.  After allowing it to go to screensaver and re-entering password, the problem returned, and was once again temporarily fixed by a minimize/restore.
Running 10.04 32bit, compiz, gnome

---

### Post by BobvanderPoel on 2011-03-24
I'm completely convinced that this is bug with compiz. I've been running for 2 days now with KDE (not compiz) with no problems. I also ran for a day with GNOME without compiz ... again no problems.

I tried to upgrade from compiz .8x to .9x but gave up :) And I have no idea of how to report the bug to someone who cares.

Hope this helps.

---

### Post by masgeeks on 2011-03-24
Hi - same thing here with the *ghost* menus, can click on the main menus but cannot select a sub menu.  10.04 Lucid 64 bit, am using Compiz.  This only began after upgrading Firefox to 4.0.

Also, off topic, but the hack from OMG!Ubuntu to reduce menu to icon (instead of text) doesn't work for me for some reason.  I still get the FIREFOX name and no icon...  Restarted Firefox but no change, maybe need to log out and log back in... will try later...

---

### Post by FreewheelinFrank on 2011-03-25
This bug definitely seems to be caused by Compiz, both in Ubuntu and Debian Squeeze (somebody linked previously to a post on the Debian forum describing the same issue).

It also affects Totem, again both Ubuntu and Debian Squeeze. Somebody filed an Ubuntu bug report but it died.

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/517207](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/517207)

I guess a bug report needs to be filed against Compiz covering Debian and Ubuntu and mentioning Firefox and Totem.

Where that would be, I have no idea.

---

### Post by TurboTippy on 2011-03-25
I have the same issue and it's definitely display related. If I minimise Firefox then maximise again all is ok. If I switch my KVM to my other pc then switch back, firefox menu's no longer work.

---

### Post by Vaphell on 2011-03-25
definitely compiz fault - somehow inactivity messes up the order of 'layers' to draw and stuff that is supposed to be on top is drawn below other windows. Focus switch (e.g. alt-tab) resets the stack and things go back to normal.
[https://bugs.launchpad.net/compiz/+bug/438868](https://bugs.launchpad.net/compiz/+bug/438868)
Of course it's a disaster that the bug goes unfixed for so long (filed in 2009).

---

### Post by TurboTippy on 2011-03-26
On my setup if I disable compiz the problem no longer occurs.

---

### Post by texla on 2011-03-26
Having the same problem - FF 4.0 and compiz running.  Minimize and restore window seems to get menus/bookmarks back in my control.  Seems like a bug in FF 4.0 to me - I never had this problem before with FF 3.6, Chrome or any other browser in Ubuntu while running compiz - There are always strange annoying bugs with every FF update - 4.0 does seem a little faster but it is annoying to me that I lose the use of my browser after every resume.

---

### Post by Vaphell on 2011-03-27
i still think that it's because of compiz, after all you disable it and everything starts to work. That bug happened with 3.6 too, but it's more blatant now. On launchpad that bug was originally filed against ff3.5. In 3.6 address bar didn't work when you typed in - layer with suggestions was not visible so you couldn't see the results. 100% confirmed, i had it countless times.

Maybe in ff4 they revamped UI framework and use different tech to draw combos, menus, live bookmarks and other stuff that is affected (different flavor of window widget or whatever) and that tech is more prone to the bug in compiz than the old way of drawing those things.

---

### Post by BobvanderPoel on 2011-03-27
Definitely compiz.

I'm sort of happy about all this. The frustration with compiz prompted me to try kde again (hated 4.0 so much!!!) ... and, well, 4.5 (ubuntu 10.10) isn't perfect, but it is very usable. I've been using it for several days now and firefox has been running perfectly.

---

### Post by platosearwax on 2011-03-27
> **BobvanderPoel said:**
> Definitely compiz.

I'm sort of happy about all this. The frustration with compiz prompted me to try kde again (hated 3.0 so much!!!) ... and, well, 3.4 (ubuntu 10.10) isn't perfect, but it is very usable. I've been using it for several days now and firefox has been running perfectly.

I've actually installed kubuntu desktop on both of my current machines and after using it for several days I am pretty happy with it as well. I was an openSUSE user for a couple of years and I actually prefer kubuntu's implementation.

---

### Post by beringse on 2011-03-27
Same here using a bluetooth mouse, menu selection disappears when I hovered over to select-tried it with a wired mouse I had laying around and the issue stopped. Weird.

---

### Post by ilcavero on 2011-03-27
As mentioned above, alt+tab fixes this for me on firefox 4 / ubuntu 10.04 x64

---

### Post by RogelioP on 2011-03-27
> I'm thinking that this is not a firefox issue? But, really don't know. 

After upgrading from FF3 to 4 I noticed the menus would not drop down after the IBM T30 (Ubuntu 10.10) would go into its screensaver and was brought back up; switching to another workspace and back, or minimizing and maximizing FF 4 or launching another application on the same workspace as FF would have the menus working again.


-- RP

---

### Post by taylortwt on 2011-03-28
I have the exact same problem since I switched to FF4.  Ubuntu 10.10 x64

---

### Post by mart1n on 2011-04-01
Same problem on FF4 only, no other application, nor on FF3.6. Running 64 bit 10.10 . restart of FF4 fixes it. I have compiz enabled.

---

### Post by paulyg on 2011-04-03
Just another datapoint. Having this issue on 10.04 32 bit + FF4. Never had this issue with FF3.6. FF restart or minimize + maximize fixes the issue. My desktop is stock Gnome with "Normal" visual effects (which I assume uses Compiz).

---

### Post by Vaphell on 2011-04-03
yes, desktop effects use compiz and believe me, you had this issue :P i certainly experienced it with 3.6, but it affected only address bar suggestions

---

### Post by manzdagratiano on 2011-04-04
I was getting ticked off by this bug and I am thankful that an ALT+TAB or a maximize-minimize workaround exists, even though I would prefer an actual solution.

On a side note, I think this is the first instance of a circular reference I have ever seen! The Debian post referred to in this thread

> **eric1959 said:**
> [http://forums.debian.net/viewtopic.php?f=6&t=61909](http://forums.debian.net/viewtopic.php?f=6&t=61909)

refers back to this thread itself! Amazing I must say (though it might be hard to appreciate) :)

---

### Post by pistachepastis on 2011-05-06
I fear it's not a compiz bug.

I miss menus in both Firefox and Thunderbird. But don't have Compiz installed.

(I am running Xubuntu Natty).

---

### Post by zoso375 on 2011-09-17
Anyone still having this issue? I'm running Natty, and it's affected me for awhile- in Firefox and Thunderbird.

---

### Post by BobvanderPoel on 2011-09-17
> **zoso375 said:**
> Anyone still having this issue? I'm running Natty, and it's affected me for awhile- in Firefox and Thunderbird.

Yes, still get it once in awhile. Maybe once a month. This is with Natty and Firefox 6.0.2. Just minimize/max and all's fine. The way firefox sucks memory is a bigger issue.

---

