---
title: "update-apt-xapi (How to disable it?)"
date: 2011-01-16
forum: General Help
---

### Post by yae7 on 2011-01-16
i am using lubuntu 10.10 on old computer and runs fine except when runs "**update-apt-xapi**" (runs daily) and consumes 100% cpu and 90% RAM!

> 
AMD Athlon(TM) XP 1800+
256 ram

Kernel: Linux 2.6.35-24-generic (i686)

Already i have tried this:
**sudo chmod 644 /etc/cron.weekly/apt-xapian-index**

but in my case, this is not a solution, because "update-apt-xapi" runs daily.

How i can solve this? because is impossible use computer when this process is running:(

---

### Post by SteveDee on 2011-01-16
> **yae7 said:**
> ...How i can solve this? because is impossible use computer when this process is running:(

I don't use Xapian on Lubuntu for this very reason, so I recommend you open Synaptic and remove it.

Otherwise read this; [http://reformedmusings.wordpress.com/2009/06/05/fixing-update-apt-xapian-in-ubuntu-9-04-jaunty/](http://reformedmusings.wordpress.com/2009/06/05/fixing-update-apt-xapian-in-ubuntu-9-04-jaunty/)

---

### Post by yae7 on 2011-01-23
i removed it and synaptic stopped working. and also it uninstalled the connection to Internet and it cannot return to installing...

Finally, i have removed lubuntu from my computer and i have instaleed puppy linux Until there is a correction for this problem

---

### Post by victorhugo289 on 2011-03-20
I have a Pentium 4 computer, 1GB ram, 2Ghz, and this thing suddenly started being a problem for me too.
I wonder how I never noticed about this program, maybe because I just put the System Monitor indicator on the top panel? yeah, that's probably the reason, because I just started noticing this thing 2 weeks ago and I have been running Ubuntu 10.10 for months!
Yeah, I don't want to disable it but I would prefer it if there was some way to manually start it, that would be nice, so that you can control it.
Well if this program has been running in the background before without me noticing then it is no such a big problem, it only lasts for about a minute or so, but it is something weird indeed.

---

### Post by Jared Norris on 2011-03-22
> **SteveDee said:**
> I don't use Xapian on Lubuntu for this very reason, so I recommend you open Synaptic and remove it.

Otherwise read this; [http://reformedmusings.wordpress.com/2009/06/05/fixing-update-apt-xapian-in-ubuntu-9-04-jaunty/](http://reformedmusings.wordpress.com/2009/06/05/fixing-update-apt-xapian-in-ubuntu-9-04-jaunty/)

I removed apt-xapian-index a long time ago and have never looked back. The only part of Synaptic that doesn't work after removing this package is the "quick search" function. The normal search works just fine. Considering I've never used the quick search function this seems an acceptable trade off for me

---

### Post by rvndrk3233 on 2011-08-15
someone sticky this for debian as well. SQUEEZE has the same issue and it boils my LT21, as well as annoys the hell out of me.

---

