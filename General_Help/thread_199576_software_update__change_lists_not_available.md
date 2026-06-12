---
title: "software update:  change lists not available?"
date: 2006-06-19
forum: General Help
---

### Post by ChrisC on 2006-06-19
My automatic weekly security update has run (breezy/5.10), and for the 4 packages that it wants to update, instead of describing the changes it says "The list of changes is not available yet. Please try again later."  It's been like that for two days now.  Anyone know of any server / repository troubles, or ... ?

---

### Post by ChrisC on 2006-06-19
anyone?

---

### Post by ChrisC on 2006-06-19
It appears to me that the software update mechanism is broken for the security updates to Ubuntu, at least to breezy / 5.10 and for at least a week.  Can anyone confirm this?  Hello? :)

---

### Post by ChrisC on 2006-06-20
OK, I will mail a $5 check to the first person to answer this question for me.  WTF.

---

### Post by ifokkema on 2006-06-20
[QUOTE=ChrisC]OK, I will mail a $5 check to the first person to answer this question for me.  WTF.[/QUOTE]
LOL, does the answer need to be helpful? :D

I've seen this, too. The exact changes are, as far as I know, not included in the standard files that are on the servers. But since it hasn't downloaded the packages yet, it must be retreived from some source other than the packages.

But even if you don't know the changes, it doesn't prevent you from updating anything, does it?

---

### Post by ChrisC on 2006-06-20
All updates have had changes listed before, and the packages this time aren't exactly esoteric (one's the kernel itself), so the fact that I don't see the text indicates that something's broken somewhere.  I'm betting that last week's Breezy security update wasn't uploaded properly.

I like to see the changes before applying the fix.  Further, just accepting problems is a bad habit to start, especially when it comes to the security update process.  Every fixed problem starts out with someone noticing it, right?  The death of a thousand cuts ...

I'm just trying to get someone to notice.  The $5 offer is still out there :)

---

### Post by Zimmer on 2006-06-20
[QUOTE=ChrisC]All updates have had changes listed before, and the packages this time aren't exactly esoteric (one's the kernel itself), so the fact that I don't see the text indicates that something's broken somewhere.  I'm betting that last week's Breezy security update wasn't uploaded properly.

I like to see the changes before applying the fix.  Further, just accepting problems is a bad habit to start, especially when it comes to the security update process.  Every fixed problem starts out with someone noticing it, right?  The death of a thousand cuts ...

I'm just trying to get someone to notice.  The $5 offer is still out there :)[/QUOTE]
 I have seen other threads (and am searching for them again at the moment) which detail unfortunate things happening in some instances if you upgrade to the new kernel. These are cured by going back to using the previous kernel. As you say, the changes are not yet listed. I was going to upgrade in the next couple of days, but I am staying with Breezy and the old kernel for the time being as I have some important work to finish...and my system is fairly stable...if I find those other posts I will note them here for reference

---

### Post by az on 2006-06-20
I asked on the mailing list.

[https://lists.ubuntu.com/archives/ubuntu-users/2006-June/083245.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-June/083245.html)

---

### Post by ChrisC on 2006-06-20
Awesome, thanks azz.

---

### Post by ChrisC on 2006-06-21
Looks like there were no responses there either  ....

/me continues dangling a $5 bill out ...

---

### Post by ifokkema on 2006-06-22
[QUOTE=ChrisC]Looks like there were no responses there either  ....[/QUOTE]
I guess people prefer answering questions to problem that seem to matter to them. I have the same problem as you, but although I prefer going through the changes first, too, I personally just upgrade either way. Whether that's smart or not can be a long debate :)

---

### Post by az on 2006-06-23
[https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/40058/+index](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/40058/+index)

---

### Post by ChrisC on 2006-06-25
Apparently fixed in the repository system, because now the change lists are showing up for these same 4 fixes (which I hadn't applied).  Probably somebody somewhere has a weekly process that got goobered up last week and then repaired this week.

It is a shame that I couldn't get an answer, even with the offer of money.

---

### Post by ChrisC on 2006-06-25
Thanks azz, I didn't see your followup post for some reason.  I expected that the fix was in the pipeline, but the silence was disconcerting ...

---

