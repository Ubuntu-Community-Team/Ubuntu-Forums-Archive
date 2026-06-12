---
title: "Firefox 3.5.7 doesn't shut down properly"
date: 2010-01-08
forum: General Help
---

### Post by Handssolow on 2010-01-08
Mostly I'm not able to properly shut down Firefox, this started after today's Firefox update to 3.5.7. If I close Firefox wait 30 seconds say and reopen it, I get a message to say it's still running. System Monitor shows that I'm using about 98% CPU. If I shut down the PC I get a report that Firefox is still running.

I can stop Firefox using System Monitor and also after a PC shutdown and reboot but even than I'm given a message when shutting down to say that Firefox is running but not responding.

Anyone else with this problem?

---

### Post by Handssolow on 2010-01-08
Firefox seems to have settled down after a re-install of Firefox 3.5.7 in Synaptic and a reboot. I'm thinking that I've not seen the last of this.

I've some evidence here to suggest that closing Firefox 3.5.7 with a right click on the lower tool bar is better than closing Firefox from the top right hand corner.

---

### Post by Handssolow on 2010-01-08
My problem with Firefox 3.5.7 is still present. After I've closed down Firefox using the top right hand corner X, System Monitor shows Firefox process is still running and using 98%-100% CPU, seemingly on one of the two cores.

So far I've not seen any similar reports of this issue with Firefox 3.5.7

---

### Post by lannatwin on 2010-01-09
Same problem here. Mint Helena.

---

### Post by darkstaar on 2010-01-09
This is often caused by extensions that may not be well written.

---

### Post by mikewhatever on 2010-01-09
What extensions do you use? Perhaps the new version doesn't like some of them.

---

### Post by lannatwin on 2010-01-09
Adblock Plus
DownThemAll
Flagfox
Ghostery
LastPass
User Agent Switcher
Xmarks

---

### Post by DustofDust on 2010-01-09
i have the same problem

someone should file a bug at launchpad

---

### Post by Handssolow on 2010-01-09
This problem still exists.
When I shut down Firefox I'm using System monitor to stop Firefox just this though doesn't enable me to restart a browser session.

After I've closed Firefox's window, if I stop and start Firefox in System Monitor I can eventually get the process to finally stop cleanly then I can start another fresh Firefox session, without having to reboot the PC.

I've got these Add-ons-
NoScript
Adblock Plus
Ghostery
Ubuntu Firefox Modifications

I've just noticed that with the upgrade to 3.5.7  User Agent Switcher has gone missing. I didn't get any notice of any incompatibility during the upgrade.

Yesterday I found someone having what appears to be a similar problem but with windoze OS, this may or may not be relevant.

Edit: The link now shows the Firefox Add-on Ghostery as the likely cause of this problem

[https://support.mozilla.com/en-US/forum/1/547799](https://support.mozilla.com/en-US/forum/1/547799)

---

### Post by Handssolow on 2010-01-09
I've re-installed User Agent Switcher after it had apparently been removed with the Firefox 3.5.7 update. It's not made any difference, I'm still left with CPU 98%-100% after I've closed the Firefox Browser window and using System Monitor to "End Process".

Edit: After I re-installed User Agent Switcher and rebooted Firefox it is currently shutting down normally, suggesting the problem is linked to this Add-on. I'll post again if the problem return.

Edit 2: Problem still occurring but not after every Firefox session.

---

### Post by mikewhatever on 2010-01-09
You could verify if any of the extensions causes the problem by running Firefox in so called safe mode with all extension and themes disabled.

firefox -safe-mode

---

### Post by Handssolow on 2010-01-09
> **mikewhatever said:**
> You could verify if any of the extensions causes the problem by running Firefox in so called safe mode with all extension and themes disabled.

firefox -safe-mode

I've run Firefox in safe mode with Add-ons disabled using the terminal command firefox -safe-mode as suggested and Firefox closed normally. This doesn't conclusively prove that an Add-on is the cause because I can sometimes run Firefox normally and close without getting stuck with 98%-100% CPU on one of the the cores.

I did however noticed this message in the terminal after inputting the firefox -safe-mode command

(firefox:3590): GLib-WARNING **: g_set_prgname() called multiple times

Is this significant?


Edit: There seems to be a similar thread reporting this problem-

[http://ubuntuforums.org/showthread.php?t=1376639](http://ubuntuforums.org/showthread.php?t=1376639)

---

### Post by nanotube on 2010-01-09
please see my post (#2) in this thread:

[http://ubuntuforums.org/showthread.php?t=1376582](http://ubuntuforums.org/showthread.php?t=1376582)

(try creating a fresh profile.)

---

### Post by noob555 on 2010-01-09
Same problem here.  I'm running the following add-ons:

[INDENT]Adblock Plus
BetterPrivacy
Flashblock (currently disabled b/c I hate it)
FoxyProxy Standard
Ghostery
Greasemonkey
printpdf
Targeted Advertising Cookie Opt-Out (TACO)
Ubuntu Firefox Modifications[/INDENT]

Nanotube, on a different thread suggested the following:

[INDENT]could be something with your profile

try starting a fresh profile, and see if the problem goes away.

(to do this, start 'firefox -P' to start the firefox profilemanager, create a new profile, start with that profile, and see if there are any problems quitting.)
[/INDENT]


I'm going to give it a try and see what happens.

EDIT: CREATING NEW PROFILE SOLVES PROBLEM.  Works as a quick fix, but now all my addons, etc. aren't there.

---

### Post by mkvnmtr on 2010-01-09
This has been a recurring problem for me for quite a while. It happened on several upgrades and I am now using 3.5.8pre and it still happens on 9.04 and 9,05. I think I will run it in the terminal and see what it says.

well that did not show anything it was the first time it shut down cleanly in a few days maybe someone else can try it and gett some feedback.

---

### Post by noob555 on 2010-01-09
So I created a new profile and now Firefox works like a charm.  

Since creating a new profile essentially does the same thing as disable all of the addons.  Based upon what people have posted above, only addons we share in common are Addblock Plus and Ghostery.  I'm going to add these one at a time and see what happens.

EDIT: I added *all* of my previous items.  Problem has not recurred, so it must be something else.  Not sure what else to do other than just move to the new profile.

EDIT: Problem was eventually reduced to GHOSTERY.  Disable or remove completely, quit out of firefox, and end the firefox process in System --> Administration --> System Monitor --> Processes

---

### Post by Handssolow on 2010-01-09
The new Test profile I created in Firefox closed down correctly but so did the couple of minutes of my subsequent default Firefox session.

I didn't like using the default session, I seem to be missing the options to accept or deny cookies amongst other things though it's partially there in Tools>Page Info. I'd made a backup of my bookmarks just in case but apologies, I'm not really wanting to customise a fresh Firefox profile unless there's no other alternative. I'll await if others identify more specifically what's causing this failure of Firefox to close properly.

---

### Post by lannatwin on 2010-01-10
It seems to be fixed for me.  Not sure why - I didn't do anything.  There were some Mint updates applied today. :?

---

### Post by nanotube on 2010-01-10
see post #11 in this thread:

[http://ubuntuforums.org/showthread.php?p=8641275](http://ubuntuforums.org/showthread.php?p=8641275)

bikehelmet has traced it down to the ghostery addon.

---

### Post by Handssolow on 2010-01-10
Yep, fingers crossed, it looks like Firefox is back to normal by disabling Ghostery, closing down Firefox (and ending the process manually) then re-enabling Ghostery.

My final comment is that I notice it takes about 15 to 20 seconds after the Firefox window closes for the firefox process to end as seen in System Monitor. CPU is about 100% during this period but at least Firefox closes down spontaneously. I suspect this is normal. All being well I'll mark it as SOLVED in a few days time.

Edited: problem not solved using the above fix. I'm going to see what happens if I disable Ghostery.

---

### Post by rookcifer on 2010-01-10
I am having the same problem.  Interestingly, I was reading a Windows forum and came across a bunch of Windows users have this issue with 3.5.7.  They had narrowed it down to Ghostery.  So, I decided to disable ghostery and restart, and sure enough, disabling Ghostery fixed it.

---

### Post by nanotube on 2010-01-10
someone should file a bug with ghostery... i used the 'contact us' form on the ghostery site, but not sure if it went anywhere useful...

---

### Post by Rodney9 on 2010-01-10
I disabled Ghostery and still Firefox v3.5.7 wont close down and use 100% of cpu.

---

### Post by lannatwin on 2010-01-11
I thought it was fixed after shutting down Ghostery and restarting Firefox and Ghostery.  After a couple of re-boots, the problem has returned. :(

---

### Post by Rodney9 on 2010-01-11
Bump We need a update

---

### Post by analoog on 2010-01-11
Instead of disabling the plugin I removed the plugin, seems to work okay now.

---

### Post by Handssolow on 2010-01-12
Since disabling Ghostery, Firefox shuts down normally. I'll keep checking if there's an update for Ghostery which clears this problem before I re-enable it.

Only Ghostery users should have experienced this specific problem with Firefox 3.5.7. It may be independent of the OS.

---

### Post by ds3 on 2010-01-12
This is definitely an identical problem in both Ubuntu 9.10 64 bit and Windows XP, so it's not the Ubuntu build that's the issue. I am running a dual boot system with a shared profile and seeing it in both operating systems. I have just disabled Ghostery and will see how that goes. I had already tried disabling a number of other addons without success.

---

### Post by Rodney9 on 2010-01-15
> **analoog said:**
> Instead of disabling the plugin I removed the plugin, seems to work okay now.

Thank You , un-installing ghostery fixed the problem.

---

### Post by acetylyne on 2010-01-16
Verified on the Ghostery site:
 
[http://getsatisfaction.com/ghostery/topics/firefox_3_6_beta_5_ghostery_not_allowing_firefox_to_be_released_high_cpu_usage](http://getsatisfaction.com/ghostery/topics/firefox_3_6_beta_5_ghostery_not_allowing_firefox_to_be_released_high_cpu_usage)
 
no response appears forthcoming?

---

### Post by 73ckn797 on 2010-01-18
Same problem. Disable Ghostery and problem fixed.

---

### Post by Handssolow on 2010-01-19
Even if they get the problem with Ghostery fixed, I'm not sure yet if I'll be putting it back.  

[http://davidcancel.com/the-future-of-ghostery/](http://davidcancel.com/the-future-of-ghostery/)

---

### Post by mechaxl on 2010-01-24
yeah, it's definitely Ghostery, fixed as soon as I disabled it.

---

### Post by khopek on 2010-02-15
No idea what Ghostery is, but I have had this issue with FireFox every since I've used Ubuntu Karmic. My FF addons include:

NoScript
Compact Toolbar
FireBug
Web Developer Toolbar

---

### Post by DustofDust on 2010-02-16
this problem is not solved. i have to kill firefox about every second time!

---

### Post by DustofDust on 2010-02-17
update from ghostery and problem is solved

---

### Post by isee on 2010-03-24
Im using Firefox 3.0.18, the default Ubuntu install, and I also had that problem of not shutting down ( a recent problem, perhaps since a firefox upgrade, I cant recall when it started exactly).  So from what I read here I redownloaded Ghostery from its website and the problem seems solved.

---

### Post by nuchdog on 2011-10-30
If you don't have ghostery installed, there are several other reasons this can happen.  The most common is that the permissions to your profile file are wrong.  Check ~/.mozilla/firefox/profiles.ini to make sure that it is read and write enabled.  If not: 

chmod 777 ~/.mozilla/firefox/profiles.ini

---

### Post by oldos2er on 2011-10-31
Closed, please don't bump old threads.

---

