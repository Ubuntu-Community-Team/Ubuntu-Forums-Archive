---
title: "Keyboard and Mouse locks up"
date: 2011-01-18
forum: General Help
---

### Post by OldManRiver on 2011-01-18
All,

Having a problem, my keyboard and mouse lock up.  The problem is consistent but timing is intermittent.  My machine with Ubuntu 9.10 sometimes locks up both the keyboard and mouse causing me to force a re-boot, with reset switch on the box.  This sometime happens within less than 15 minutes, out to over 5 days, but always eventually occurs.

I need to know if anyone else has had this and what the solution was.

I did not find anything doing a search, but may not have entered the right keywords.

Thanks!

OMR

---

### Post by xob on 2011-01-18
Does ctrl-alt-F1 works? Then you can restart your desktop, type ps -A | grep desktop and than kill the process.
My Samsung laptop have the same thing when I want to change the brightness.

---

### Post by OldManRiver on 2011-01-19
> **xob said:**
> Does ctrl-alt-F1 works? Then you can restart your desktop, type ps -A | grep desktop and than kill the process.
My Samsung laptop have the same thing when I want to change the brightness.

XOB,

Nope, that does not work, keyboard is totally locked when is locks up.  I also tried the ctrl+alt+backspace to see if the X-Win would restart and nothing.  No other combinations produce anything either.  Hard restart is the only thing that clears it.

OMR

---

### Post by OldManRiver on 2011-01-20
All,

I'm not sure if this is caused by some downloaded javascript, but it seems to become more prevalent when the browser is open.

OMR

---

### Post by xob on 2011-01-20
I'm not sure if there is a log somewhere, so you could trace it. On my laptop keyboard and mouse locks when I press FN + brightness up/down. I think it is some sort incompatibility with laptop...

---

### Post by OldManRiver on 2011-01-23
XOB,

I'm either always using the mouse, not the keyboard, or the machine has been setting idle, when the lockup occurs, so not a key combination, putting me in this state.

That is why, since occurs most often with browser open, I'm thinking some javascript.

Is there a way to track javascripts that are open and operating?  the system log just shows the browser as the process, unless I'm missing something.

OMR

---

### Post by xob on 2011-01-23
Mozilla has an error console in Tools menu. You can also try to disable JavaScript to test if this is the cause.

---

### Post by OldManRiver on 2011-02-08
> **xob said:**
> Mozilla has an error console in Tools menu. You can also try to disable JavaScript to test if this is the cause.

XOB,

I proved, to myself, that the lock-up only happens when the browser is open.  My default mode had alway opened the browser, so I did not do this and ran CAD apps, games, etc with no problems.  Within 5-10 minutes after I open the browser the lockup occurs.


OK, not noobie, but this is going to sound like it, how do I get this done?  Mostly wanting to stop the JS.

I went to "System" + "System Monitor" and I do not see the JS runniing, with or without the browser so what do I look for?

Thanks!

OMR

---

### Post by OldManRiver on 2011-02-09
XOB,

Strange, since I opened the System Monitor, the system is not locking up, regardless of what I do.  As I say the JS is not showing and I wonder if there is something that happens when the System monitor is open that prevents it from running, as now I can not get the system to crash.


At this point I thinking this is interesting enough to submit a bug ticket into the Ubuntu bugzilla, as maybe having several others trying to reproduce this error will help us trap and fix it.

What do you think?

OMR

---

### Post by OldManRiver on 2011-02-11
All,

So with "System Monitor" open the keyboard and mouse have not locked up even once, for more than 48 hours now.

Wonder what is different with the SM open?

OMR

---

### Post by SuperSeki on 2011-02-11
hey...been using 10.10 for a couple days now (first time Ubuntu User).  But now, my mouse works...but i can't type anything.  I cant even click on the Menus in the Panel.  They don't open.  Nothing opens except programs locked to the panel.  I'm thinking that it may have something to do with my mousepad lock/unlock button.  I'll try it after I post this.

Edit:  Yes.  After I hit my mousepad unlock/lock button...there was a quick glitch on the screen and everything locked up.  The keyboard wouldn't type or respond.  Mouse cursor still moved...but could not open the menus...could only launch apps that are on the panel.  This just started happening this morning.  The last thing I did last night was to install VLC through Package Manager.

---

### Post by OldManRiver on 2011-02-14
All,

I posted at:

[http://ubuntuforums.org/showthread.php?t=1670299](http://ubuntuforums.org/showthread.php?t=1670299)

and had the system lockup again 3 times.  Noticed that when I started using the 2nd workspace, the instability came back.

Anyway due to all the restarts I lost all my DT icons, all my work sessions no longer have the top bar with the window sizing buttons, etc. (so I can not resize or move any of the open windows/session); and my 2nd and 3rd workspaces went away, leaving me only one workspace.

Wondering how I recover from this?  I tried restarting several times and did not get a recovery.

Thanks!

OMR

---

### Post by OldManRiver on 2011-02-14
All,

Started using multiple workspaces and then boom, the lockups came back.

Wondering if I need a re-install of the OS?

OMR

---

### Post by OldManRiver on 2011-02-15
All,

Went to the bootup menu and performed the recovery, but that did not help.

I think what I am facing are some X-Win parms.  Does anyone know what these are and howto correct these?

Thanks!

OMR

---

### Post by OldManRiver on 2011-02-15
All,

Read my post at:

[http://ubuntuforums.org/showthread.php?p=10460734#post10460734](http://ubuntuforums.org/showthread.php?p=10460734#post10460734)

I'm only partially functional right now, without extra workspaces, drag/drop/window sizing and nothing on the task bar to switch between apps.

Thanks!

OMR

---

### Post by sydbat on 2011-02-15
You shouldn't post the same problems in multiple threads.

That said, we need more info from you so we can help diagnose what is happening.

What is your computer hardware? CPU, RAM, Graphics card, etc?

Also, you are using 9.10 (if I read correctly). I believe that it's life-cycle is coming to an end and will no be longer supported after April. Depending on your hardware, you should upgrade to 10.04 at least, as it is the current LTS.

---

### Post by howefield on 2011-02-15
Threads merged.

---

### Post by OldManRiver on 2011-02-16
All,

I got the keyboard and mouse lockup resolved by upgrading to 10.04, but the DT problem still exists and it keeps saying I do not have a "Windows Manager".  

I figured out that is due to a conflict somewhere between the standard DT Windows Manager and Compiz.

Do not know what or where to look to resolve, but when I go to Compiz and click on it I get the missing Windows wrappers back.

Let me know if you have a clue to what is needed here.

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-20
All,

With WebAdmin installed will finish backups soon and do fresh install with whole disk format.  Hope this fixes it all.

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-02
All,

After the install things settled down.  Just waiting to make sure I have solid 2-4 weeks operation before declaring this resolved.

Thanks!

OMR

---

### Post by xouns on 2011-05-03
To bad I only see this now (one day to late), reinstalling Compiz might work. On my laptop with 10.10, it sometimes failed to launch the top of the windows, too. Restarting compiz (alt-F2, compiz) would fix it for me. Minor nuisance, but a nuisance nonetheless. Fixed by an update, I guess.

---

### Post by OldManRiver on 2011-05-04
> **xouns said:**
> To bad I only see this now (one day to late), reinstalling Compiz might work. On my laptop with 10.10, it sometimes failed to launch the top of the windows, too. Restarting compiz (alt-F2, compiz) would fix it for me. Minor nuisance, but a nuisance nonetheless. Fixed by an update, I guess.

xouns,

Do not know if I made it clear, but I had to revert to 9.10 to get this stable.  I have several threads open on this at:
[LIST]
[*]Here
[*][http://ubuntuforums.org/showthread.php?t=1690652&page=2](http://ubuntuforums.org/showthread.php?t=1690652&page=2)
[*][http://ubuntuforums.org/showthread.php?t=1710539](http://ubuntuforums.org/showthread.php?t=1710539)
[*][http://ubuntuforums.org/showthread.php?t=1684144&page=3](http://ubuntuforums.org/showthread.php?t=1684144&page=3)
[/LIST]

and still have issues with Samba, PAM Keyring and Sound but those are separate issues from the Keyboard and Mouse issues, so opening separate threads on them to work off individually.

Additionally I have an AirLink 101 4 Port KVM in my configuration now and it still looses the keyboard, when switching from machine to machine, but that is only issue with the KVM, which needs the external power supply to resolve that issue as it is a power level issue from the KVM that looses the keyboard def to the machine, when I switch away from it.

Glad my postings helped you to.

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-07
All,

I think I have a Eureka moment here.  I now know that the machine is stable, hardware, software, etc.  But I still have this problem.

What I found is that when I go to certain websites and they have java phishing scripts, some of which are written for Windows, and these try to embed themselves and find things on my box, then the instabilities come back.

Rest of the time all is stable.  Just trying to remember, log and avoid these crap phishing sites.  This may have been my problem before, but remember then it was happening all the time, whether browser was open or not.

Still watching this and will report back soon!

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-19
All,

I was running system test on another box for an audio problem, so noticed the video testing and ran it.  These instabilities showed right away.

Testing, for video, starts with the highest resolution and works down.  Only the first 3 passed and then the system went out, so think I found this problem.  Whenever a program tries to call the lesser res, this box bombs.

Anyway was used to looking in xorg.conf (I think) for resolutions to eliminate the lesser res defs, but cannot find that on my box.  Where are they hiding the X11 res defs?

Thanks!

OMR

---

### Post by lmn. on 2011-05-19
there is a firefox addon called noscript which removes all javascript from webpages.
if it is java causing the problem, this will fix it.    

*you mention it is more prevalent while the browser is open, assuming it  happens regardless of this.. it is unlikely java is causing it..

if  you use ff, try the addon anyway, its great :D

like crashed said, have you  narrowed it down to a problem with the OS, the USBs or the mouse/kb  itself??

---

### Post by crashed111 on 2011-05-19
I have seen similar problems in around 10 Dell machines which were caused by dodgy capacitors and it looks like your issue could be similar. If a reinstall does not fix it you may be looking at a hardware issue.

---

### Post by OldManRiver on 2011-05-21
> **lmn. said:**
> there is a firefox addon called noscript which removes all javascript from webpages.
if it is java causing the problem, this will fix it.    

*you mention it is more prevalent while the browser is open, assuming it  happens regardless of this.. it is unlikely java is causing it..

if  you use ff, try the addon anyway, its great :D

like crashed said, have you  narrowed it down to a problem with the OS, the USBs or the mouse/kb  itself??

lmn,

Worse with KVM in the CKT, but the resolution testing showed the lower res defs to be problematic.  Will install the noscript addon, hate all the keystroke tracker anyway.

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-21
> **crashed111 said:**
> I have seen similar problems in around 10 Dell machines which were caused by dodgy capacitors and it looks like your issue could be similar. If a reinstall does not fix it you may be looking at a hardware issue.

crashed111,

Would the capacitors be on the video board or the motherboard?

Thanks!

OMR

---

### Post by OldManRiver on 2011-06-04
crashed111,

Was looking for a response, please.

OMR

---

### Post by PGFracing on 2012-03-31
Did anyone find out what is causing this. Mine happens before I even open anything. It locks up sometimes and sometimes doesn't also doesn't show Ubuntu name when it boots.

---

### Post by OldManRiver on 2012-04-02
All,

Added a new video card, based on the advise about the capacitors, and now is stable.  Have another box with exact same problem and original setup so will add PC slot VIC to it, sure it will also "fix", so marked this one "SOLVED"!

Thanks!

OMR

---

