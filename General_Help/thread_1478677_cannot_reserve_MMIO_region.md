---
title: "cannot reserve MMIO region"
date: 2010-05-10
forum: General Help
---

### Post by wigglestix on 2010-05-10
I updated my laptop to 10.04 earlier today and it worked fine but it was being a bit glitchy so i rebooted my laptop and it worked fine until it showed an error saying "cannot reserve MMIO region".

---

### Post by dcstar on 2010-05-10
> **wigglestix said:**
> I updated my laptop to 10.04 earlier today and it worked fine but it was being a bit glitchy so i rebooted my laptop and it worked fine until it showed an error saying "cannot reserve MMIO region".

It is just a kernel message, a message that can be ignored as it does not do anything to your system.

---

### Post by wigglestix on 2010-05-10
Yes i do realise this because after the message showed up i started pushing every button on my keyboard i somehow got it to boot past the message but before discovering this it would not boot past this on its own.  So i guess my question is, is there a way to make it so it boots past this next time because i am not currently able to restart my machine without pressing random buttons to try and get my machine to continue booting?

-thanks Kristian

---

### Post by dcstar on 2010-05-10
> **wigglestix said:**
> Yes i do realise this because after the message showed up i started pushing every button on my keyboard i somehow got it to boot past the message but before discovering this it would not boot past this on its own.  So i guess my question is, is there a way to make it so it boots past this next time because i am not currently able to restart my machine without pressing random buttons to try and get my machine to continue booting?


Just because you see that message it does not mean that it has anything whatsoever with your current problem.

---

### Post by wigglestix on 2010-05-10
Ok. So is there any way to figure out what is wrong possibly by looking at one  of the log files?

---

### Post by Docaltmed on 2010-05-18
> **dcstar said:**
> It is just a kernel message, a message that can be ignored as it does not do anything to your system.

Why does ubuntu produce messages which look like error messages which are intended to be ignored?

---

### Post by memius on 2010-08-17
I have the same problem. The boot process stops after 'Cannot reserve MMIO region'.

If the problem has nothing to do with the message, where do we look, and what do we look for?

I have not been able to boot the machine at all, even when pressing random keys.

---

### Post by KutViZ on 2010-09-18
I guess you have somewhat different problem than we have. I read that thing every time but it doesn't stop booting.

---

### Post by mikeeve on 2010-11-10
Just reinstalled Windows 7 and then Ubuntu. Upgraded Ubuntu from 10.04 to 10.10 (actually, it was a new install from the Live CD; I did not upgrade over the old install), and now I'm getting 'cannot reserve MMIO region'. I have no idea what it means. Ubuntu did start with a 'disks need to be checked' message a little while ago. (  I have applied all important updates to 10.10.)  No other problems that I have noted. Ubuntu boots successfully after the message.

---

### Post by SonyFoLife on 2011-01-03
The same thing Happens to me, But then the machine boots normally.
This happened when i installed 10.04, Reinstalled 10.04, AND when i updated (through the old install) to 10.10 Maverick
i figured it was just part of the Ubuntu Boot process :shrug:

---

### Post by manchildjr on 2011-01-05
Yeah I think it may have to do with Toshibia satelites me and my freind runs ubuntu (i run 10.10, he runs 10.04) and we both get it but it still boots. I get an 8-bit ubuntu logo though.

---

### Post by manchildjr on 2011-01-05
I know i just poseted but what is MMIO

---

### Post by demon148 on 2011-01-28
Can I ask how many of you are using ATI Graphics cards when you are getting this message. I have a ATI card and I get the message as soon as I put in a Nvidia card the message goes, although the message doesnt cause any problems to my system the message does annoy me and I do want to get rid of it.

---

### Post by demon148 on 2011-01-30
Ok so I think it may also have something to do with older AMD hardware as I have moved the ATI Graphics Card to another AMD Motherboard with a skt a processor from a Slot A and it worked without any problems.

---

### Post by bestgun on 2011-02-07
> **demon148 said:**
> Ok so I think it may also have something to do with older AMD hardware as I have moved the ATI Graphics Card to another AMD Motherboard with a skt a processor from a Slot A and it worked without any problems.

I'm in the list. I have an old AMD with an ATI 9200 graphic card.
Anyway the message is the only annoyance, everything else seem to work properly.

---

### Post by mikeeve on 2011-02-07
> **demon148 said:**
> Can I ask how many of you are using ATI Graphics cards when you are getting this message. I have a ATI card and I get the message as soon as I put in a Nvidia card the message goes, although the message doesnt cause any problems to my system the message does annoy me and I do want to get rid of it.

I use onboard video from the AMD 785 chipset.  I've accepted the message like I've accepted wearing glasses. Que sera, sera  etc.

edit: changed word 'error' to 'message' in above (as indicatd by dcstar, below. thanks, mate!)

---

### Post by dcstar on 2011-02-08
> **mikeeve said:**
> I use onboard video from the AMD 785 chipset.  I've accepted the error like I've accepted wearing glasses. Que sera, sera  etc.

It is **not** an error", it is simply a message. Why do people complain about things that have absolutely no effect on their systems?

---

### Post by spacesamurai on 2011-03-06
Just had a similar problem when updating to 10.10. I found that the error message had no relation. For me, it was a graphic driver problem. I just dropped the box to single user and reinstalled the driver.

---

### Post by riverfr0zen on 2011-03-20
> **demon148 said:**
> Can I ask how many of you are using ATI Graphics cards when you are getting this message.

Yeah, same here. Well it took so long to actually get ATI working, I now have some weird relationship with the manufacturer. Stockholm syndrome, maybe.

---

### Post by donec on 2011-03-27
Here is some information that helped me understand the when this message is shown it is not due to a fault of the machine but due to a response to an included process which is there for developers.

[http://lwn.net/Articles/270939/]("http://lwn.net/Articles/270939/")

---

### Post by riverfr0zen on 2011-03-27
> **donec said:**
> Here is some information that helped me understand the when this message is shown it is not due to a fault of the machine but due to a response to an included process which is there for developers.

[http://lwn.net/Articles/270939/]("http://lwn.net/Articles/270939/")

Thanks. Was getting lost there.

---

### Post by snatale42 on 2011-04-11
> **dcstar said:**
> It is **not** an error", it is simply a message. Why do people complain about things that have absolutely no effect on their systems?

Because it was obviously designed to look like an error. It's annoying. Before the driver you have a splash screen, after you have text which stops at the top of your screen, and pauses long enough that you can read it. Thats what errors do, not information thats ignorable.

---

### Post by CarlosFerreira on 2011-07-25
I have the same problem (spanking new 4-core AMD processor and ATI graphics card). It will not boot after the message and, annoyingly, I can't install it.

It's probably something deep within Natty; I've tried installing Mint, and the same thing happened.

In short: Help! My new laptop is stuck on running Windows!

---

