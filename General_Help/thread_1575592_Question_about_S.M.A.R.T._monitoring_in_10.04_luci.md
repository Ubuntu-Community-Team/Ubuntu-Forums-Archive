---
title: "Question about S.M.A.R.T. monitoring in 10.04 lucid"
date: 2010-09-16
forum: General Help
---

### Post by dwhitcombe on 2010-09-16
I had a computer running Koala next to my new, spiffy Panasonic plasma, and, in order to stream Netflix on it, it was either put windows on it, or move my ancient Mac G4 into the TV room. As the tv-room box was a tiny little (and cute, I might add) Atom box, I sort of sighed, and installed XP on it. (sigh).
It had (both running Koala and XP) a Seagate FreeAgent 1TB USB for putting media on. 
Then, on Tuesday, I bought a BluRay player with built-in Netflix support, and, whoohoo! I can put linux back on the little atom. So I brought the 10.04 Lucid disc into the TV-Room, installed, and am greeted by the "disk failure imminent warning. 

I looked at the S.M.A.R.T. data using the Disk tool in Lucid, and see (get this) 5.8e12 seek errors.
That's 5.8 trillion seek errors in 119 days of being powered on.
That works out to a little more than 580,000 errors PER SECOND for the life of the drive.

Is there some error in Lucid's interpretation of the S.M.A.R.T. data? 

That number just can't be right.

580,000 seeks per second... I'd be able to pick up the noise of the head moving around on an AM radio (580KHz).
And that's 580,000 FAILURES per second, continuously, for 119 days.

Owing to the possibility that maybe the drive is failing, I'm backing it up to a different drive, and it's just churning away (been copying steadily since about 2:00 PM MDT today, it's currently 22:00, and in 8 hours, it's copied 80 gigs, and the seek error number isn't climbing.

Is there a bug in Lucid's interpretation of the Smart Data?

(Bona fides: I installed Slackware on a PC using 32 floppy images copied to a NeXT Magneto optical disk once. I mounted the floppy images on an NFS network in the house running Clarkson packet drivers under DOS 5.0. This was in 1992, and it was my own 'cube.)

Edit: "))

---

### Post by CharlesA on 2010-09-16
Was that being reported on the external drive? I know those can be a bit flaky, as I've only been able to get a "OK" result from running SMART tests on the seagate external drives I have. Internal drives are fine.

What interface is it? USB? It should definitely be copying faster then 80GB in 8 hours, unless it's running off a USB 1.1 controller.

---

