---
title: "Ubuntu suddenly unstable."
date: 2010-02-11
forum: General Help
---

### Post by whitefort on 2010-02-11
Hi,
I'm just wondering if anyone else is experiencing this:

Over the past few days (across three computers) Ubuntu sometimes suddenly seems to crash, dropping back to the login screen.

The first time it happened it was on an older machine, and I thought it was maybe just the hardware.  Then it happened on a different machine, and now it's just happened on my main PC (lots of work lost! Grr...)

This has never happened with ubuntu before, and since one of the PCs has a plain ubuntu installation with no software or tweaks added, I'm just wondering if something in a recent update might be causing the problems.

Anyway, am I on my own, or has anybody else noticed this?

Thanks!

---

### Post by t0p on 2010-02-11
I see you use Karmic.  Are all three of the machines running 9.10?

---

### Post by akakingess on 2010-02-11
Also, have you tried using the next older kernel to see if the problem still persists or only happens in the most recent kernel? It's easy enough to try by just choosing the older kernel when the GRUB menu is up.  Worth a shot and a good way to troubleshoot/narrow down the problem.

---

### Post by whitefort on 2010-02-11
Yes, all Karmic, all running perfectly until this week.

And so far the crash (if that's what it is) has only happened once on each machine.  I presume if it was a general Ubuntu bug, there'd be lots of posts about it here, but that's not the case.  

It appears to have started after the recent updates, but I suppose that could be just a coincidence.

I also considered that it might have been some sort of temporary interruption of our electricity supply, but presumably that would hit all the computers at once (not to mention the clocks, VCRs etc.)

An occasional crash isn't the end of the world, I just wondered if anyone else was getting it.

---

### Post by whitefort on 2010-02-11
> **akakingess said:**
> Also, have you tried using the next older kernel to see if the problem still persists or only happens in the most recent kernel?

Excellent idea - I'll bear that in mind.
The thing is, the problem is (so far) so infrequent that it would be hard to know if a different kernel was really a cause or cure.

I stress that the problem is very infrequent - one of the PCs is on nearly 24/7, and it's only happened once.  It's just odd that all three machines hiccupped inside a few days.

If this was my windows machine, I wouldn't even consider it unusual.  It's just that I don't think I've EVER had Ubuntu crash on me before.

I haven't run any updates on my laptop for about a month.  I'll update it today, then leave it running to see if it develops the problem.

---

### Post by pfranks on 2010-02-11
Login screen - The GUI screen (Gnome/KDE) or black text fullscreen? Are you seeing evidence of a reboot, or a direct jump to login info (logout?), or as if the entire GUI had terminated and restarted? 

If you didn't reboot, does "uptime" on the 24/7 machine show a reasonable time since boot??

I have no idea what the answers will mean yet, just fishing for clues.

---

### Post by whitefort on 2010-02-11
> **pfranks said:**
> Login screen - The GUI screen (Gnome/KDE) or black text fullscreen? 

Hi,

No, it's not a full reboot - it's just dropping out to the GUI Gnome login screen - as you say, as if the GUI had restarted.

Uptime isn't reset by the 'crash'  and still shows the full length of time the machine has been running.

I'm not sure it's going to be possible to really troubleshoot this unless it starts happening a lot more often (only once on each machine over a couple of days so far). 

I want to stress, this isn't a biggie for me. I just wondered if anybody else had encountered it.

If it had only happened on one machine I would have thought, "HUH." and ignored it.But it  struck me as odd that it hit three of them.  Maybe I'm just unlucky!:D

---

### Post by pfranks on 2010-02-12
> **whitefort said:**
> If it had only happened on one machine I would have thought, "HUH." and ignored it.But it  struck me as odd that it hit three of them.  Maybe I'm just unlucky!:D

Just wondering if the default hotkey mapping for GUI kill and restart has been changed from Ctrl+Alt+Backspace - or duplicated to a different key. I agree it is suspicious you saw the same issue on multiple machines, and your description fits for a logout or restart. 

On a side note, it looks like 9.04 on my new toy (Dell Latutude 2100) doesnt respect Ctrl+Alt+Backspace. Either it is broken in 9.04 or Dell decided to mess with the defaults :(

---

### Post by whitefort on 2010-02-13
> **pfranks said:**
> Just wondering if the default hotkey mapping for GUI kill and restart has been changed from Ctrl+Alt+Backspace... Either it is broken in 9.04 or Dell decided to mess with the defaults :(

I'm a little out of my depth here, but I seem to recall that it was Canonical who decided to mess with the defaults, by disabling that Ctrl+Alt+Backspace thingie.

(Yeah, the same thought had occurred to me - had I accidentally hit the 'forbidden' keys?  But even if they still worked, the odds of a couple of users here accidentally suddenly doing it for the first time seemed a bit slim.)

---

### Post by pfranks on 2010-02-14
> **whitefort said:**
> I'm a little out of my depth here, but I seem to recall that it was Canonical who decided to mess with the defaults, by disabling that Ctrl+Alt+Backspace thingie.

(Yeah, the same thought had occurred to me - had I accidentally hit the 'forbidden' keys?  But even if they still worked, the odds of a couple of users here accidentally suddenly doing it for the first time seemed a bit slim.)

I had missed that Canonical screwed with us. Thanks.

I was thinking more along the lines of one user (or app) inadvertently remapping things. OTOH if it has still only happened once on each machine... not broken don't fix until it is reproducible.

---

