---
title: "Some General Issues I've been having :("
date: 2009-08-21
forum: General Help
---

### Post by beastrace91 on 2009-08-21
First off I really love Ubuntu - I've had only Linux installed on my system for the last year now and for the last 7 months my distro of choice has been Ubuntu.

How ever two weeks ago I got my new Sager laptop (with a blank hard drive) and promptly installed Ubuntu 9.04 64bit on it. I have been having a few issues in these past couple weeks. It is super sluggish when loading X for the first time, once X starts and I hear the audio play there is still another 20 seconds or so before the Gnome menu bar is fully loaded. How ever is I restart X (from a tty login) it comes up in about half the time. I have never had this much of a speed difference in the past (between X starting the first and second time). Also I have had the system completely freeze on me twice (nothing responds, can't drop down to a terminal login ect.) where I have to cold shut it off. And I've also had issues with it hanging at shutdown, it fully shuts down but does not actually power off...

I know these are kinda general issues and there isn't much to pin-point the issues but I am happy to do debugging work to help solve them. I'd love to stick with Ubuntu instead of distro-hopping again.

~Jeff

---

### Post by P4man on 2009-08-21
Hmm.. I had never even heard of "sager" before, and now there are 3 or 4 threads in a matter of day of sager owners having weird issues with jaunty:

[http://ubuntuforums.org/showthread.php?t=1232587&highlight=sager](http://ubuntuforums.org/showthread.php?t=1232587&highlight=sager)
[http://ubuntuforums.org/showthread.php?t=1195654&highlight=sager](http://ubuntuforums.org/showthread.php?t=1195654&highlight=sager)
[http://ubuntuforums.org/showthread.php?t=1238076&highlight=sager](http://ubuntuforums.org/showthread.php?t=1238076&highlight=sager)

I dont want to blame a manufacturer I dont even know, but is this coincidence?

Perhaps it could be worth checking out a sager forum and see if anyone is having more luck there running ubuntu.. ? Im wondering if there is something in the recent kernel(s) that doesn't play nice with sager bios..

---

### Post by beastrace91 on 2009-08-21
I'd be willing to bet its a coincidence - if you hunt around online there are threads all over Linux forums about every different brand of laptop out there almost having some form of issue with some form of Linux.

~Jeff

---

### Post by P4man on 2009-08-21
> **beastrace91 said:**
> I'd be willing to be its a coincidence - if you hunt around online there are threads all over Linux forums about every different brand of laptop out there almost having some form of issue with some form of Linux.

~Jeff

Im not saying sager are the only one's with problems on linux (at all)  but its gotta be a small vendor compared to dell / toshiba / lenovo etc, and really, I've only seen sager posts recently with issues I can't explain at all or that I think have something to do with ACPI. 

That might even not be Sager's fault, but .. well, its a bit many to be a coincidence IMHO. If in the mean time there had been 10 such posts for Dell machines, I might not have made that link, but there hasn't been even one.

Anyway, I can only suggest trying what i suggested in those other threads. Try the "nuclear" option of turning ACPI off with a kernel parameter (acpi=off), or the less drastic "noapic" and "nolapic" switches. Try an older or newer kernel. Try an updated bios. File a bug report.

---

### Post by P4man on 2009-08-21
did some more googling and found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217849](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217849)

In there, you may find something worth trying. Like adding: 

"clocksource=jiffies"

and

"acpi_skip_timer_override  lapic=debug"

To your kernel parameters. And let me know if it helps. If so, I can put it in the other threads as well, as I suspect you're all having a very similar problem.

---

### Post by beastrace91 on 2009-08-21
I'll try adding those kernel parameters later today and let you know if it helps, I'd like to point out though I have a Sager NP8662 laptop (the other threads are having issue with Sager 2000 series models) and that my install goes perfectly but the system is hanging while running.

~Jeff

---

### Post by P4man on 2009-08-21
yes, but its not at all unlikely a vendor reuses large parts of its bios code across different models. And I would have guessed an acpi problem even without having read "sager" anywhere, as its the most common cause of unpredictable freezes and those kernel switches may help on any machine where there is a kernel/acpi bios problem. In that thread there are some other kernel switches that where proposed, that didn't work for those people, but that you could try as well if these dont help.

Of course, you can always file your own bug report, especially if none of these solutions would help.

---

