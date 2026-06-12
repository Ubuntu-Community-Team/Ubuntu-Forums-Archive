---
title: "printer not connected?"
date: 2009-10-04
forum: General Help
---

### Post by dief-eh? on 2009-10-04
Hello
My HP LaserJet 4plus, which was working fine last week, has become invisible to the operating system, an otherwise up-to-date Intrepid Ibex. 

I first noticed the problem trying to get my timesheet spreadsheet printed to take to work on Oct 1. The panel printer icon would display briefly, and mousing over it would display the message that the printer was 'probably not' connected. The HPLIP device manager listed "Device communication error". 

Polling Google/these forums/hp-check.log for info brought up the possibility that recent 'upgrades' may have removed or otherwise disabled a number of programs, routines/scripts such as: debus; cups-devel; libcrypto; SANE, among others (14 errors, total!)

I have checked and rechecked the parallel cable connections both to the printer and to the back of the computer case. No obvious changes from the week before, or indeed from the past few years, would seem to have occurred. 

I swapped out the 4-plus' parallel cable for my IIIp cable, but got the same errors.

My next thought is to reboot using a PuppyLInux, or TinyMe CD to check the physical connections. 

Any ideas why my printers might stop working this way, or how to check that the connections?

---

### Post by StuartN on 2009-10-04
> **dief-eh? said:**
> Any ideas why my printers might stop working this way, or how to check that the connections?

I once clicked on the option to remove packages that were "orphan" or "redundant" or some word like that and many days later happened to notice that I couldn't print to the network laser, and only a couple of weeks later did I put two and two together. I think in my case that because I did a manual install of the very latest HPlip from the HP website that Synaptic did not recognize dependencies and let me clean up something that was required.

---

### Post by dief-eh? on 2009-10-04
> **StuartN said:**
> I once clicked on the option to remove packages that were "orphan" or "redundant" or some word like that and many days later happened to notice that I couldn't print to the network laser, and only a couple of weeks later did I put two and two together. I think in my case that because I did a manual install of the very latest HPlip from the HP website that Synaptic did not recognize dependencies and let me clean up something that was required.

Thank you v. much for your reply. I don't remember removing any redundant orphans within the past few years. (Maybe it's time?!) I did manage to pretty much hose my then system a few years back with FSLint, but that experience certainly scared me away from housecleaning, not that I needed much convincing.

I had looked at the HP website, and noticed that the version Synaptic had installed was (I guess) a couple of iterations back of the pack. But I'd resisted the impulse to try to install the newer version mostly because the dependency issues you mention exceed my ability. :c)

HP's diagnostic tool (hp-check -t), though, listed fourteen(!) broken or non-existent dependencies, several of which Synaptic doesn't mention. I really don't know what to do with info though. Over the years, Ubuntu's weekly up-grades have sometimes 'broken' some minor peripheral function, but the opensource 'hive mind' seems able to patch the inconsistencies quite quickly, often within hours. Perhaps I've gotten too comfortable with just hitting 'upgrade-now' and enjoying the idea that something in my life is "up to date"! 

Still, I can't believe the up-grade process hasn't noticed a problem with a reasonably common printer family, or that I'm the only person with a couple of elderly HP lasers that the operating system no longer 'sees' because a baker's dozen dependencies have fallen off the back of the truck? 

And this experience suggests that many of us no longer use a printer frequently enough to notice a malfunction soon enough to easily diagnose the problem ourselves. 

Thanks again for your reply.

---

### Post by StuartN on 2009-10-04
> **dief-eh? said:**
> I really don't know what to do with info though.

I just uninstalled CUPS and HPlip, then reinstalled CUPS from Synaptic and installed the latest HPlip from the HP website. I am far too lazy to fiddle with dependencies, but it worked absolutely fine. The printer and scanner work brilliantly over the network, although I have no idea why I might want to scan a document in another building!

I see I have a few things called "Installed (local or obsolete)" or "Not installed (residual config)", some of which I don't recognise at all, and will not be clearing them out.

---

