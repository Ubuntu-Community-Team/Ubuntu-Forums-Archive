---
title: "Configuring Radeon 3650"
date: 2009-12-13
forum: General Help
---

### Post by polarberg on 2009-12-13
I've had continuous headaches trying to configure my system for an ATI Radeon 3650 graphics card on a Lenovo ThinkPad. I regularly run into Ubuntu running in "low graphics mode" because the driver isn't configured correctly. Some of the configurations I have run, particularly with fglrx, are disastrous, occasionally ending in a bash prompt which blinks so bad I'm all but forced to reinstall.

I've been searching for a right answer for about two months now to no avail. ATI configuration appears to be a common problem, but none of the solutions I've seen so far work. I don't even know if it's my particular card that's the problem, or the software available.

My computer has successfully rendered Compiz effects, though the computer was very slow when it did this. I've also had GL running, but my second-to-last configuration couldn't manage that. In attempting to fix *that* configuration, I've broken the driver entirely, and I'm not sure how to restore my previous settings, let alone get the thing working properly.

To be specific: Everything was working fine, *except for* GL, desktop effects, and putting Flash into fullscreen (possibly unrelated), up until I started trying to specify
```
Driver "ATI"
```in my xorg.conf. I can't revert to my previous settings, which I believe had me on the radeon driver.

Is there any way to configure this card so that things like 3d acceleration, GL, desktop effects, etc. work properly? If not, can someone help me figure out how to at least get back to running at full resolution?

---

### Post by cporter23 on 2009-12-13
When I received my new Dell studio xps 16 (same vid card as you), I had trouble with the ati driver.  Compiz was really slow.  Took me a couple of days to find it, but my solution was to install the latest binary driver from the ati website, and install xorg with the no-backfill patch.  That sorted out my issues.  It doesn't appear I'm permitted to post links, so you'll have to google bug number 351186 in the launchpad and go down to post 86 for a link to a repo with xorg compiled with the no-backfill patch.

---

