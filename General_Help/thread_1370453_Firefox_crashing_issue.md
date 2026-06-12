---
title: "Firefox crashing issue"
date: 2010-01-02
forum: General Help
---

### Post by bravo sierra echo on 2010-01-02
I'm getting an issue where Firefox will lock up completely and go grey and unresponsive.  Looking at the process list in the system monitor then shows it as "uninterruptible" and there is no way to kill it - close and kill process produce no effect at all.  You then can't open a second copy, because you get the "Firefox is already running..." error message.

The only way to get it back seems to be to restart the machine.

It appears to be happening at random - sometimes straight away, sometimes after a couple of hours of browsing, and on all sorts of different websites.  Other software doesn't do this, only Firefox.

Anyone got any ideas?

Ubuntu Gnome 9.10, kept updated, on a 3.00ghz machine with 1.5 gig of RAM.

---

### Post by kiridude on 2010-01-02
I had a similar issue on another machine that turned out to be caused by too many connections on my bit torrent client. Are you running something else that could be eating a lot of bandwidth?

Also, what command are you using to kill firefox?

---

### Post by mrfnuts on 2010-02-25
I have been having similar issues since Version 8.  It just started one day and has followed me with all my upgrades up to Ubuntu X64 V 9.10 now.  It's actually starting to get very frustrating.  

Firefox will go gray, and lock up for seconds to nearly a minute at a time, and in the process list say 'uninterruptible'  But, what's worse it causes anything else I'm running (of which these days not much at one time) to also lock up and go gray and normal, gray and normal, _even the system monitor!!_

I am not even sure if it's firefox that's doing it anymore, but, my only clue is if I have a couple tabs open on a site that uses flash.

I am actually at my wits end on this and getting ready to go back to Windoze.  

If anyone has seen this behavior before, I would really appreciate a solution.

---

### Post by dcstar on 2010-02-25
> **bravo sierra echo said:**
> I'm getting an issue where Firefox will lock up completely and go grey and unresponsive.  Looking at the process list in the system monitor then shows it as "uninterruptible" and there is no way to kill it - close and kill process produce no effect at all.  You then can't open a second copy, because you get the "Firefox is already running..." error message.
........

Rename the existing profile in the .mozilla folder and start Firefox so it creates a fresh one.

If things then work ok you either have a corrupt original profile or some add-ons that may be causing the problem.

---

