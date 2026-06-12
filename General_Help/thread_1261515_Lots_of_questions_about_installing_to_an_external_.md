---
title: "Lots of questions about installing to an external HDD, for cross-platform use"
date: 2009-09-08
forum: General Help
---

### Post by mailman1175 on 2009-09-08
Apologies in advance: This post may get long, and it's very broad, topically speaking. Parts of it could probably fit in a number of places, but it's necessarily addressed as a whole, so I can't really split it up until I know a bit more.

So here's the story: I have a 1TB external hard drive that my wife and I share the old-fashioned way. I said to myself the other day, "Self, wouldn't it be cool if you could have a portable 1TB Ubuntu system that you could boot anywhere?" Even better, wouldn't it be cool to have the option to boot a 32-bit or 64-bit system from the same hard drive. *Even better*, I thought, I could boot my new MacBook to Ubuntu without endangering the hard drive! Seemed like a cool set of ideas, so I set out to git 'er done. Famous last words, right?

I already had an 8.04 image, and a 32-bit 9.04 image; I downloaded a 64-bit 9.04 image. I figured I'd end up using Hardy for older machines and 64-bit Jaunty for newer ones and my MacBook. I did a little bit of research (not enough, apparently, as is now obvious), but honestly, it never occurred to me that I might have problems with trying to install Hardy to an external drive. I did at least decide that the whole process would be easier and less risky running from a Live DVD on my wife's native Ubuntu machine than it would be to endanger my new MacBook (my dedicated business machine) with this little venture. 

Anyway, I ended up b0rking the install on my wife's Hardy Heron laptop. Grub would get to stage 1.5, then throw error 21; my patience with fixing the problem ran out before I found a solution. I spent a couple more hours jacking with it, then decided I'd be time ahead just to do a clean install. I've re-installed Hardy now, and the machine's in the office, downloading that first massive update. Not that big a deal, really, although time-consuming. I've determined that installing Ubuntu to an external hard drive is not nearly as open-and-shut as I thought it was. 

All of which leads me (finally, I know) to a couple of questions I'd never have thought of if I hadn't screwed up the first time. Two basic questions, I think:

----   I gather that it is possible to install to and run some versions of Ubuntu from an external drive. My poking around after the fact turned up a lot of references to Grub 2, and to its ability to boot from external drives. It's packaged with Jaunty and Karmic, I see, so I wonder if I'd have avoided at least this first catastrophe by attempting the install from one of those versions. Is this true (at least in theory)?

----  The second question is, "How portable would such an installation truly be?" I mean, there's Sugar and PenDriveLinux, right? I'm just expanding that idea out, in terms of portable storage, by a couple orders of magnitude. Is it possible to install 2 or 3 Ubuntu variants to the same external drive, such that I can boot them from any machine capable of booting from USB, be it Mactel, Wintel, or AMD, 32- or 64-bit? [Does hardware configuration happen at install, or at boot-up? Put another way, will I have to reconfigure for hardware every time I boot up on a new machine, or can I expect the Ubuntu variant to "figure out" what it's working with?] Let's say I even go so far as to put 3 variants on the drive: One for 64-bit Mactel machines, one for 32-bit Wintel machines, and one for 64-bit Wintel machines. Realistic? Or am I missing something essential in the way these operating systems install and run?



Like I said, I know this is kind of all over the place, but I'm curious. Takers?

---

