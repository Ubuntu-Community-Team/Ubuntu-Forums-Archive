---
title: "browsers crashes the whole system"
date: 2009-12-16
forum: General Help
---

### Post by oblomir on 2009-12-16
I have ubuntu 9.10 AMD64 installed on my desktop(Athlon X2 6000+, Gigabyte MB ga-m790x-ds4, 4GB ram, Gigabyte Radeon HD4850 512MB). 

When surfing with either Firefox(3.5.5) or Opera(10.10), after a while the browser window freezes, and whatever I do to attempt to close or kill it(or even if I do nothing) makes Ubuntu freeze completely(I can move the mouse about, but can't click or anything, no keyboard shortcuts work, can't switch to console, the only solution is a hard reboot).

I've only recently upgraded to 9.10, so I did a clean install to make sure it's not an upgrade problem, but the issue persists. 

I also have ubuntu 9.10 x86 on my laptop(Thinkpad R50e), and I've been running it since release, but the problem doesn't occur there. 

I'm assuming it is an issue with flash and AMD64 as it happens on both browsers and while various different websites are loading.

After a hard reboot when I load the *exact same* websites that caused the crash nothing happens, and everything loads perfectly so I cannot reproduce the problem, but it always happens randomly.

Any ideas?

---

### Post by akakingess on 2009-12-16
First thing that I look at with random freezes like that would be RAM, so it might be beneficial to run a MEMTEST the next time you boot up.

---

### Post by oblomir on 2009-12-16
> **akakingess said:**
> First thing that I look at with random freezes like that would be RAM, so it might be beneficial to run a MEMTEST the next time you boot up.

It's not a hardware problem, 9.04 ran fine just last week.
I did test it just to make sure, everything checks out.

---

### Post by akakingess on 2009-12-16
I wasn't trying to immediately blame your hardware (although it can just suddenly crap out on us), but rather just trying to get a starting point, now we can at least say that we know it is not the RAM.

---

### Post by istor on 2009-12-16
The same exact problem and here... The cpu monitor still works but i can't do anything. The mouse is working, i making mouse over items and i get the tag description but nothing from clicking... i having randomly freezing issue. 

any idea after the hardware issue?

---

### Post by istor on 2009-12-16
It might not be a problem with the browser. I see that the mail client might cause it.
Is it possible? when storing the drafts etc. At the freeze time i saw a process in the footer saying sth like "drafts saved"

I am using thunderbird 3 right now. This also happened with Evolution mail

---

### Post by istor on 2009-12-17
i searched the forums about other freeze issues and i found that the problem may consist because of your graphic card. I switch of the visual appearance to "none" from "custom" and now i get no crashes till now. 

Follow the path system/preferences/appearance/visual effect
and check none.

---

### Post by oblomir on 2009-12-18
> **istor said:**
> the problem may consist because of your graphic card. I switch of the visual appearance to "none" from "custom" and now i get no crashes till now. 


Thanks. Seems to be working so far.

And another question:

If it does turn out to be the problem with the visual effects settings and ati hd4850 card which seems likely at this point, where do I report the problem so that it can hopefully be fixed in future?

---

### Post by ruario on 2009-12-19
It might be two different lock up bugs (one in FF and one in Opera) and it is just a coincidence you are hitting them both.

What you are seeing with Opera might be [this]("http://my.opera.com/community/forums/topic.dml?id=336001").

---

### Post by chillyomi on 2009-12-19
try using chrome for linux

---

