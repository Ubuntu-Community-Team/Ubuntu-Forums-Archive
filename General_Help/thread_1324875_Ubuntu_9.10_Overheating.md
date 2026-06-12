---
title: "Ubuntu 9.10 Overheating"
date: 2009-11-12
forum: General Help
---

### Post by Vince N on 2009-11-12
Hey guys,

I was hoping some kind soul would be able to help me.

I've been running Ubuntu on my laptop for about 2 years.  My laptop is an Acer Aspire series and aside from the normal annoyances here and there configuring things it has run Ubuntu pretty solidly up until the 9.10 release.

For some reason my system runs real hot under 9.10 and the fans are almost always going full bore.  That's just sitting idle.  Doing anything moderately processor intensive causes it to overheat.  Running flash video for any amount of time causes the safety shut down to trip.

I cleaned the laptop out but I maintain it pretty well so there wasn't much dust or anything in there.

Running it under Windows or 9.04 DOES NOT cause the laptop to overheat.  Indeed it runs a good 10 to 15 degree's cooler at idle and doesn't spike up much at all when under load.  This makes me believe that the OS is the culprit.  But why?  And how do I fix it.

9.10 looks pretty nice but this is a total deal breaker for me.

---

### Post by Vunutus on 2009-11-12
Have you checked the system monitor or the top command to see if any particular processes are going crazy?

---

### Post by Vince N on 2009-11-12
Yes, And most everything sits idle except firefox which will run up to around 50 to 90% when running flash video of any kind.

---

### Post by DeMus on 2009-11-12
> **Vince N said:**
> Yes, And most everything sits idle except firefox which will run up to around 50 to 90% when running flash video of any kind.

Did you install the right driver for your graphics card?

---

### Post by Vince N on 2009-11-12
It's a cheap integrated Intel card.  I don't think there are any proprietary drivers for it.  It's using the same default drivers as it was under 9.04.  Also all features work and its at native resolution.

---

### Post by Vince N on 2009-11-15
Bumping for great justice.

---

### Post by Vince N on 2009-11-15
Just in case anyone else stumbles upon this I think I may have found the issue.

Apparently the issue has to do with some kernel updates that were done that caused the fan support in the Acer Aspires to regress causing the fans to slow down or not work at all.  They have a fix in place with a newer kernel that's not part of the main repositories yet.  I'm running it right now and my CPU is running much cooler though I haven't tested it under load yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)

---

### Post by alex30002 on 2009-11-16
i had the same problem too with an aspire 5315 espacially when i was waching youtube. it suddenly shut down. i realize that it is really hot

---

### Post by mjwhitfield on 2009-11-17
> **alex30002 said:**
> i had the same problem too with an aspire 5315 espacially when i was waching youtube. it suddenly shut down. i realize that it is really hotSame laptop, same issue. Gonna check out Vince N's fix now.

---

### Post by mjwhitfield on 2009-11-17
I'm gonna try updating the BIOS via a freedos usb stick as suggested in the bug comments to see if that helps. Failing that I'm going to try the recompiled kernel.

---

### Post by mjwhitfield on 2009-11-18
The following fixed the problem for my Acer Aspire 5315:


Downloaded this ISO (it's just freeDOS + the BIOS updater):
[http://www.lesgrosbarbares.info/flashbiosacer_v1_43.iso](http://www.lesgrosbarbares.info/flashbiosacer_v1_43.iso)

Burned it, switched my BIOS to boot from CD first and booted off the CD. It boots and updates by itself, be careful as after the BIOS is updated it reboots so you need to get the CD out the drive pretty quickly.

Hope this works for other 5315 owners.

---

