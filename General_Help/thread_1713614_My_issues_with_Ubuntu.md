---
title: "My issues with Ubuntu"
date: 2011-03-24
forum: General Help
---

### Post by DipreSantana on 2011-03-24
I've been using Ubuntu 10.10 64 for about 8 months now.  It's pretty enough, fast, and I love never having to worry about one of my brothers plugging in their infected computers into my network and taking my machine out.

Now, there are some issues, big ones.

My swap keeps disappearing, I can't get my machine to hibernate.  Flash sorta works on 64, but there are too many bugs.  Sometimes my left mouse button just stops working after suspending the machine.  The machine seems to have a mind of its own, I'll wake up and find all kind of apps open, and new folders everywhere.  The battery life is horrendous, on Win 7 I'd get about 4.5 hours, with Ubuntu I'm lucky to get 2.5, the fingerprint scanner will work for a few months and then just stop recognizing my prints.

I've tried to fix all these issues countless times, but have never been able to.  I need help.

---

### Post by hakermania on 2011-03-24
I read threads like this one and i'm wondering why I have an Ubuntu 10.10, free of bugs, and not complaining why Ubuntu 10.04 where much better (i don't mean that you're complaining in any way).

Well, I won't consider myself lucky, but you, unlucky :)
AFAIK, search for all the available hardware drivers you find and install them.... This may solve some issues...

---

### Post by malspa on 2011-03-24
That sounds awful, DipreSantana. I don't think I'd put up with all that. Have you tried reinstalling? And was your md5sum okay? Other than that, nobody'd blame you for checking out some other distro...

---

### Post by beringse on 2011-03-24
Have you tried backing up your home folder/personal files then doing a reinstall? Reason I'm asking is that I had to do this a while back, after having similar issues, thereafter 10.10 has worked fine.  
Good luck

---

### Post by Another Monkey on 2011-03-24
What hardware?
What partitioning? i.e. Did you do it yourself?
What HDD configuration?  Is it Intel fakeraid (unlikely, reads like a laptop)?  Linux **does not** like that.

Backup your "/home".
Backup your Windows data (if dual booting).
Look-up details on your specific hardware to see what others recommend.
Download 10.10 (you might want to take the minimal, I had lots of problems with the 64-bit alternate failing).
Wipe the installation (be careful of your boot sector if dual booting).
Install using the advice/information you have found (e.g. 16gb for system at start of disc, 2xmemory for swap at end of disc, everything else for home*).
And go through things one step at a time.
Don't jump from one problem to the next, multiple changes will confuse things.  Focus on one, fix that, move on.  If you struggle, try here or #ubuntu on IRC with questions about that one problem.

Battery: the hardware is specifically optimised for Windows, but the usual tricks of reducing brightness, disabling WiFi, Bluetooth etc and spinning the discs down when possible should help.

*There are many, many options and opinions on partitioning, it all depends on what you are doing.  For general use, just let the installer do it.

---

### Post by DipreSantana on 2011-03-24
My machine is a laptop with a C2D and 4 Gb ram, 250GB HDD, I let the installer do it's thing, about 2 months after the hibernate option disappeared, a after searching and searching, turns out that the Swap just stops working, so I deleted the partition, added in a new one, and modified the fstab, it worked, for about 2 days, after wards it disappeared again.  All the other issues I have no idea about, all the drivers are working correctly as far as I can tell.

---

### Post by Spyderkid on 2011-03-24
If your using 64bit that would dramaticaly reduce your battery and some programs have compatibility problems with 64bit if you are then i suggest re-installing to 32bit.

---

### Post by Another Monkey on 2011-03-24
> **DipreSantana said:**
> My machine is a laptop with a C2D and 4 Gb ram, 250GB HDD
I meant what exact make and model.  That's what you need in order to go looking for advice/tips.  Others may have had the same issues.

It's not that I don't believe you, but I have never heard of swap vanishing.  That's pretty major!

> **Spyderkid said:**
> If your using 64bit that would dramaticaly reduce your battery and some programs have compatibility problems with 64bit if you are then i suggest re-installing to 32bit.
Really?  Got any idea why?

---

### Post by DipreSantana on 2011-03-24
> **Another Monkey said:**
> I meant what exact make and model.  That's what you need in order to go looking for advice/tips.  Others may have had the same issues.

It's not that I don't believe you, but I have never heard of swap vanishing.  That's pretty major!


Really?  Got any idea why?

HP TC4400.

[img]http://i55.tinypic.com/x58e1h.png[/img]

---

