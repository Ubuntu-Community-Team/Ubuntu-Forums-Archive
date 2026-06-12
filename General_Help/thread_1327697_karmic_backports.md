---
title: "karmic backports"
date: 2009-11-15
forum: General Help
---

### Post by Romanrp on 2009-11-15
should i enable karmic backports (unsupported updates) in the ubuntu software repositories?

---

### Post by wilee-nilee on 2009-11-15
I always do even with karmic but use your own reasoning on this.

---

### Post by coffeecat on 2009-11-15
Have a look at this:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

Backports seems safe, but do read what is says about proposed updates. I know you didn't mention proposed updates, but I've seen a lot of threads over the years from people who have enabled the proposed repository who then grumble when their system breaks.

---

### Post by autonomy on 2009-11-15
good thread, I still hadn't changed my jaunty backports and partners to karmic

---

### Post by Pjotr123 on 2009-11-15
Backports are generally less risky than proposed, but I advise against backports as well. Only use backports when you have a very good reason for it, for example a new piece of software that you really need.

---

### Post by Romanrp on 2009-11-16
I enabled the proposed updates thinking it was safer than back ports.
It updated my kernel.
I think I will keep it checked and I will also check the backports.
Thanks!

---

### Post by coffeecat on 2009-11-16
> **Romanrp said:**
> I enabled the proposed updates thinking it was safer than back ports.
It updated my kernel.
I think I will keep it checked 

Aaarrrggh! If you don't want to take well-intentioned advice, that's your privilege. After all, it's your broken machine, not mine. :| Proposed versions of kernels are often problematic.

From the link I posted:

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.

---

### Post by Pjotr123 on 2009-11-16
coffeecat +1

I would say it even more severely:

Proposed is *only* meant for testers; people who help the developers of Canonical with testing and bug hunting. Not for normal use. Never use it on a production machine.

---

### Post by skymera on 2009-11-16
I've enabled proposed, backports etc in all my Ubuntu distros (7.04, 7.10, 8.04, 8.10, 9.04 and now 9.10)

never had a fault

---

### Post by Pjotr123 on 2009-11-16
> **skymera said:**
> I've enabled proposed, backports etc in all my Ubuntu distros (7.04, 7.10, 8.04, 8.10, 9.04 and now 9.10)

never had a fault

Then you've been incredibly lucky, almost unbelievably. So far....

I've done my share of bug hunting with packages from proposed, on a test machine, and I've experienced frequent breakage. Not only on the early Ubuntu's (5.10, 6.06), but also with 7.10 and 8.04. Then I stopped with testing proposed packages and started helping in other fields.

---

### Post by 3rdalbum on 2009-11-16
> **Pjotr123 said:**
> Then you've been incredibly lucky, almost unbelievably. So far....

I've done my share of bug hunting with packages from proposed, on a test machine, and I've experienced frequent breakage. Not only on the early Ubuntu's (5.10, 6.06), but also with 7.10 and 8.04. Then I stopped with testing proposed packages and started helping in other fields.

I've used Proposed from 8.04 onwards, no problems at all.

Proposed did not exist before (I think) 7.04. It was created as a response to a situation where an update completely broke Xorg for most users; the idea being that in future such an update would hit Proposed first, the bleeding-edge people would find the problem and report it pronto, and it would never go to the majority of people.

---

### Post by Pjotr123 on 2009-11-16
Yes, well, I may have my version numbers wrong. I remember the xorg outage in 6.06 though (broke my xorg as well, but I had a recent image from Acronis, thank God).

Anyway, I had proposed turned on for some time, and experienced problems regularly. :p

---

### Post by Romanrp on 2009-11-16
hhhmmm.I think I would rather disable the proposed updates.
For the past few week I installed a new os every 3 days.Now i am back to where I started.
I can't bear any more new installs so I will turn proposed off.
No need to risk it.
Thanks!

---

### Post by autonomy on 2009-11-16
> **Pjotr123 said:**
> Only use backports when you have a very good reason for it, for example a new piece of software that you really need.
Thanks, I commented them out by the way.

---

