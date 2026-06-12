---
title: "How to prevent apps from taking all the resources?"
date: 2012-07-18
forum: General Help
---

### Post by zoffix on 2012-07-18
Hey,

How do I make it so that a single app could not kill my entire system just by taking all the RAM?

Often times a rogue app starts to chew up all my RAM and by the time I realize it, my hard drive is swapping faster than a swingers couple and several seconds later even my cursor is not responding.

I found this page, but it talks about limiting particular apps:
[http://en.kioskea.net/faq/3786-limiting-the-resources-of-ubuntu](http://en.kioskea.net/faq/3786-limiting-the-resources-of-ubuntu)

However, how to do this globally, so that any app that behaves in a dangerous way would be killed?

I believe something like this was a default in the days of Edgy, as my IRC bot would often get killed by the system if it ran too long (it had a memory leak). What happened to that? Another move closer to being Windows?

---

### Post by sgage on 2012-07-18
> **zoffix said:**
> Hey,

How do I make it so that a single app could not kill my entire system just by taking all the RAM?

Often times a rogue app starts to chew up all my RAM and by the time I realize it, my hard drive is swapping faster than a swingers couple and several seconds later even my cursor is not responding.

I found this page, but it talks about limiting particular apps:
[http://en.kioskea.net/faq/3786-limiting-the-resources-of-ubuntu](http://en.kioskea.net/faq/3786-limiting-the-resources-of-ubuntu)

However, how to do this globally, so that any app that behaves in a dangerous way would be killed?

I believe something like this was a default in the days of Edgy, as my IRC bot would often get killed by the system if it ran too long (it had a memory leak). What happened to that? Another move closer to being Windows?

I have never had this happen to me in many years of using Ubuntu. I guess the first thing to do is ascertain which program is responsible. "Often times a rogue app" isn't really much to go on - I would guess that you have one application with a problem. There just aren't hordes of rogue apps lurking out there... :KS

---

### Post by zoffix on 2012-07-18
> **sgage said:**
> I have never had this happen to me in many years of using Ubuntu. I guess the first thing to do is ascertain which program is responsible. "Often times a rogue app" isn't really much to go on - I would guess that you have one application with a problem. There just aren't hordes of rogue apps lurking out there... :KS

No, it happens with different apps, and it has more to do with, say, opening too big a file with GIMP, or what happened this morning: Firefox opening an HTML file with a ton of images.

If it were just one app, I could well use the method described in that link I mentioned in OP.

---

### Post by zoffix on 2012-07-18
Put it another way:

On my webserver that runs some flavour of Linux, if I run any script that's resource heavy, it gets killed without so much as a how do you do...

How to implement that policy on my Ubuntu box?

---

