---
title: "Updates slow down computer"
date: 2009-09-03
forum: General Help
---

### Post by Tipped OuT on 2009-09-03
Every time there's a new update available, my computer slows to a crawl for about 2-3 minutes until finally the update manager window pops up. If I decide to install the update/s... I have to stop what I'm doing, until it finishes the update/s, because my computer pretty much comes to a dead stop. I'm just wondering if this is normal?

---

### Post by dearingj on 2009-09-03
I've never seen this problem. What hardware are you using? Have you installed any unusual software?

---

### Post by Tipped OuT on 2009-09-03
634 MB's of RAM

Pentium 4 3.2 Ghz

---

### Post by dearingj on 2009-09-03
> **Tipped OuT said:**
> 634 MB's of RAM

Pentium 4 3.2 Ghz

That doesn't sound like a lot of ram for a computer new enough to have a Pentium 4 processor. I'd suggest upgrading to at least 1 GB. You'll notice a significant speed improvement if you do that.

---

### Post by fuzzman54 on 2009-09-03
> **dearingj said:**
> That doesn't sound like a lot of ram for a computer new enough to have a Pentium 4 processor. I'd suggest upgrading to at least 1 GB. You'll notice a significant speed improvement if you do that.

I have a laptop that has 465mb of RAM and a Pentium 4 that's only 2.8ghz. My system doesn't have this problem so I don't think your analysis is correct. 

Tipped Out, what processes do you normally have running?

---

### Post by Tipped OuT on 2009-09-03
> **fuzzman54 said:**
> I have a laptop that has 465mb of RAM and a Pentium 4 that's only 2.8ghz. My system doesn't have this problem so I don't think your analysis is correct. 

Tipped Out, what processes do you normally have running?

Doesn't matter what processes I have running, it's always like that. It's just the normal default Ubuntu installation, nothing added at all.

The only program I'd have running would be firefox, for example, and then an update becomes available and the system comes to a crawl. It's sickening. That's my only problem with Linux so far. :(

---

### Post by misterfixit on 2009-09-03
> **Tipped OuT said:**
> Doesn't matter what processes I have running, it's always like that. It's just the normal default Ubuntu installation, nothing added at all.

The only program I'd have running would be firefox, for example, and then an update becomes available and the system comes to a crawl. It's sickening. That's my only problem with Linux so far. :(


What type of connection to the Internet do you have?  It's possible that Update is hogging the bandwidth and causing a general slow down of the system while the system is waiting for a time out.  I have always had that problem with BitTorrent (see my other posts on that subject).  I have never experienced the slow down effect with Update, however, but I think that if there are connection problems that may be a possibility.

HTH, YMMV

---

### Post by Tipped OuT on 2009-09-03
> **misterfixit said:**
> What type of connection to the Internet do you have?  It's possible that Update is hogging the bandwidth and causing a general slow down of the system while the system is waiting for a time out.  I have always had that problem with BitTorrent (see my other posts on that subject).  I have never experienced the slow down effect with Update, however, but I think that if there are connection problems that may be a possibility.

HTH, YMMV

Wireless. It's laptop I'm using. I also have a direct connection (Ethernet cable) but I only use that for when I have no WIFI drivers and I need to download them.

---

### Post by cdbitesky on 2009-09-03
What graphics card are you running? I had a similar problem when i had a radeon card with the proprietary drivers installed.

---

### Post by Tipped OuT on 2009-09-03
> **cdbitesky said:**
> What graphics card are you running? I had a similar problem when i had a radeon card with the proprietary drivers installed.

ATI Radeon 9100/9000 IGP 128 MB's

---

### Post by cdbitesky on 2009-09-03
What drivers are you using for the card?

---

### Post by Tipped OuT on 2009-09-03
I'm not sure. I don't know if they're open source or if they're proprietary. They come with the Ubuntu installation.

Is there any way of checking?

---

### Post by cdbitesky on 2009-09-03
I find that the linux drivers installed through the update manager or from the ati website that a significant change in some kind of windows cause a huge lag spike until the process finishes. I also had the issue of the computer nearly freezing when I attempted to restore a minimized window. 
I have not found a fix for this unfortunetly :(. I uninstalled all drivers and although i have no 3-d effects of any kind, my pc runs smoothly.

---

### Post by misterfixit on 2009-09-04
> **cdbitesky said:**
> I find that the linux drivers installed through the update manager or from the ati website that a significant change in some kind of windows cause a huge lag spike until the process finishes. I also had the issue of the computer nearly freezing when I attempted to restore a minimized window. 
I have not found a fix for this unfortunetly :(. I uninstalled all drivers and although i have no 3-d effects of any kind, my pc runs smoothly.



My experiences also.  I've posted about this issue back in August.  I've stopped doing ANY "full updates" and I am not updating my kernel at all.  I update one at a time.  There is a serious issue with drivers or something that effects some people but not all.  So far, I've not seen any maintainer comments on this problem.

See this thread:  [http://ubuntuforums.org/showthread.php?t=983459](http://ubuntuforums.org/showthread.php?t=983459)

HTH, YMMV

---

### Post by Tipped OuT on 2009-09-04
Glad to hear it's not just me having this problem. Hopefully it will be handled in Karmic Koala.

---

