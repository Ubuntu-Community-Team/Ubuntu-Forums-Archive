---
title: "Thinking of Creating a Four-Seat System"
date: 2010-05-11
forum: General Help
---

### Post by zean on 2010-05-11
I've been looking around for trying to build a computer for my family, and given that multiple people want to be on at once, I've been thinking of the idea of creating a Four-Seat multiseat system. I think that, given the odd nature of what I want to do, I'll need to build this system myself. I know that multiseat systems are not very well supported in Ubuntu, so, for this thread, I'd like to focus on two things:

First, the hardware side of things. It looks like I'll need to buy 4 graphics cards, and get a motherboard with enough slots for these cards. Given that 4 people will be using the computer at once, I'll probably need at least 4 gigs of ram, and a quad-core processor.

Second, the software side of things. I need to know what sort of things I'll need to get, what I'll have to do with X. I'm lucky in that we're on 10.04 LTS, so since this is a long-term support system, we just need to get this all working on 10.04, and can let it sit for 2 years or so.

---

### Post by prshah on 2010-05-11
> **zean said:**
> given that multiple people want to be on at once, I've been thinking of the idea of creating a Four-Seat multiseat system. 

looks like I'll need to buy 4 graphics cards, at least 4 gigs of ram, and a quad-core processor.


I suggest you will be far better off building a single powerful system, and then 4 thin clients. See the community documentation for [UbuntuLTSP]("https://help.ubuntu.com/community/UbuntuLTSP") for more information and to see if it is suitable for your use.

---

### Post by JedMeister on 2010-05-30
> **zean said:**
> I've been looking around for trying to build a computer for my family, and given that multiple people want to be on at once, I've been thinking of the idea of creating a Four-Seat multiseat system. I think that, given the odd nature of what I want to do, I'll need to build this system myself. I know that multiseat systems are not very well supported in Ubuntu, so, for this thread, I'd like to focus on two things:I think that it's a great idea too but as you say, it's not all that well supported in Ubuntu (at least not in 10.04 - seems like support was much better in earlier versions).

> **zean said:**
> First, the hardware side of things. It looks like I'll need to buy 4 graphics cards, and get a motherboard with enough slots for these cards. Given that 4 people will be using the computer at once, I'll probably need at least 4 gigs of ram, and a quad-core processor.Take all this with a grain of salt because I've never run a multiseat PC, but i do have a bit of experience with different hardware. AFAIK 2 dual head cards should be able to work (rather than 4) and you'd probably get away with a higher end dual core CPU assuming your users won't be doing anything too full on (although quads are getting quite affordable now  and better is better!) 4 GB RAM sounds good but from what I've heard the main bottleneck you get with multiple seats is HDD usage. Perhaps consider at least 2 separate HDDs (one each for each users home folder or perhaps consider RAID?

> **zean said:**
> Second, the software side of things. I need to know what sort of things I'll need to get, what I'll have to do with X. I'm lucky in that we're on 10.04 LTS, so since this is a long-term support system, we just need to get this all working on 10.04, and can let it sit for 2 years or so.Now this is the tricky bit. I've searched fairly extensively online and while I've found [a blog]("http://multiseatonlinux.blogspot.com/") where a guy claims he's got it going (with plans to post a how-to) I am yet to see an explanation of how its done...just quite a few people having trouble trying to get it to work! 

OTOH If you're willing to settle for 2 seat or willing to pay and you're running 32 bit 10.04 then [Userful Multiplier(TM)]("http://www.userful.com/products/userful-multiplier") may be an option for you. The 10 seat trial version is in the multiverse repo. According to [this]("http://packages.ubuntu.com/lucid/userful-multiplier") it has a nag screen which can be removed; either by registering for the free 2 seat license or paying for a 10 seat license. I haven't tried it because I've got 64 bit and am otherwise very happy. I'd be very interested to hear how others go if they try it.

---

