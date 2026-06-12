---
title: "High CPU"
date: 2009-12-02
forum: General Help
---

### Post by judge jankum on 2009-12-02
Finally got a system to install, but in system monitor it shows from 80 to 100% cpu usage with nothing running but system monitor.
 I'M running Xubuntu 8.04... on a frankenstein'd computer lol!!!
AMD 380 
256 ram

---

### Post by judge jankum on 2009-12-03
help"

---

### Post by DeMus on 2009-12-03
> **judge jankum said:**
> Finally got a system to install, but in system monitor it shows from 80 to 100% cpu usage with nothing running but system monitor.
 I'M running Xubuntu 8.04... on a frankenstein'd computer lol!!!
AMD 380 
256 ram

Can you post a screendump of system monitor?
Before doing that, double click on the header of the CPU column (where it says %CPU) to sort the list with the programs taking the most of the cpu listed on top.

---

### Post by judge jankum on 2009-12-03
How do I get a screen shot in Xubuntu?

---

### Post by prions on 2009-12-03
Applications > Accessories > Screenshot

Or press alt+f2 and type in screenshot

---

### Post by judge jankum on 2009-12-03
Can't seem to get a screen shot. But the only thing that shows to be running is
gnome-system-monitor going from 21% to 100% looks like an EKG...Then on the resource page it goes to 100%
Everything is sleeping except system moniter

---

### Post by judge jankum on 2009-12-03
Checked after restart and still 80 to 100% cpu with nothing running except system monitor

---

### Post by jerome schatten on 2009-12-03
> **DeMus said:**
> Can you post a screendump of system monitor?
Before doing that, double click on the header of the CPU column (where it says %CPU) to sort the list with the programs taking the most of the cpu listed on top.

I have the same problem... dual core, 32bit, 9.10. Every so often after compute intensive operation, the cpu usage never returns to where it was but hangs around 75-80%. Screenshot attached:

udevd(s)  seems to be the big user, but what in heavens name is it doing? 

Any ideas appreciated.

jerome

---

### Post by winotree on 2009-12-03
The only times I've noticed it is *just after an update* when Synaptic Package Manager is going through a resorting of its search index [look in the Quick Search box].  Could this be the same issue either of you are experiencing?

---

### Post by jerome schatten on 2009-12-03
[B]Winowtree Sez:
Re: High CPU[/B]
 		"The only times I've noticed it is *just after an update* when Synaptic Package Manager is going through a resorting of its search index [look in the Quick Search box]. Could this be the same issue either of you are experiencing?"

Are you suggesting that after Synaptic is done working that your CPU usage stayed high until you shut down?  If so, it is basically the same result I'm getting.

I get it most of the time if the 'Ant with the searchlight' screensaver has deployed, or after transferring several gigs of files across my lan, or after a long streaming video (several minutes or more).  Killing Xorg and then bringing it up again didn't reset the cpu usage, so I concluded that it wasn't an Xorg problem. That's as far as I got troubleshooting it. 

jerome

---

### Post by winotree on 2009-12-03
It may stay up for a few moments but once or twice I've had to shut it down, *it* being Update Notifier, *but there weren't any updates* -- I'd just installed them.  This all happened after the fact.  

As I mentioned the high-user was the search database reseting itself.  I don't use screen savers, streaming, etc., and this had never been an issue for me -- I only mentioned it because you guys had experienced something similar to what I had and thought it may be an option to search.  

I'll wait to see whether it's something of concern or not -- once or twice is only an irritation for me but what y'all are experiencing sounds like it's more than that.

EDIT - I need to read about the relationship [if any] between Update Notifier and the search database.  Other than **Google**, any ideas?  ;)

---

### Post by jerome schatten on 2009-12-04
I did some more testing and here's a temporary work-around that doesn't require rebooting the machine:

**sudo killall udevd**

Kills the offending instance of udevd and respawns the udevd process with the cpu usage returning to normal. Other processes remain as they were and the screen stays in tact.

Of course this is not really a fix as whatever set it off in the first place is likely to set it off again.  That said, if I don't deploy the 'Ant' screensaver described previously, it rarely happens.  

BTW, I never see this problem with 9.04, only with 9.10.

Hopefully, this situation will right itself with advancing patches. 

jerome

---

### Post by Flying caveman on 2009-12-04
I'm running Ubuntu 9.10 on my laptop.  I've had some moments where my computer doesn't respond too.  I am running 'folding at home' and have desktop effects enabled.  The last time this happened guess what screensaver was trying to run?  The 'ant with searchlight' one.

---

