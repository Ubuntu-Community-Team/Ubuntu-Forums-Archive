---
title: "Many rx sky2 errors, very slow ethernet, not Marvell's fault"
date: 2011-07-05
forum: General Help
---

### Post by youWho on 2011-07-05
Not sure if "general help" is the right place for this, but it might be...

I was having such slow ethernet that it was almost unusable. Logs revealed *many* errors that said something like "... rx error; sky2 <something> expected <something> received <something> ..." the odd point being that (sorry) the problem seems to be so fully solved that I can no longer find examples in the logs to quote from. I believe that the fact that I recently installed Natty Ubuntu Studio from scratch is why I no longer have any old logs either---I had been using Maverick Ubuntu Studio. *But* I can assure you that the problem was *not* solved just by switching to Natty. If you are experiencing this you probably know generally what I'm talking about.

I think many posts in various forums blame Marvell for these troubles (I think unfairly at least in my case).

lspci shows this for my system:
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)

The reason I wanted to post this is that I had searched high and low and tried *everything* but no solution. I was in fact trying to compile a driver I downloaded from Marvell's site, but that wasn't working, and that's when in desperation I connected the new DSL bridge (DSL modem?? Not a router but looks like it could be one? The typical thing the phone companies deliver for DSL service) that the phoone company had just delivered and the problem seems to have been *totally* solved. I'm *sorry* that this post is so vague!!! But I thought I should post it anyway just in case it helps somebody.

I should add that I'm writing this from Berlin, Germany and the telephone company at this place is called "Alice". The phone connection happens to be ISDN but I honestly think that the real culprit was that the old gear provided by "Alice" years ago was no longer valid---with their service. I blame "Alice" fully for this annoying problem, because they never alerted the people living here to any problems, and indeed the problem was there, getting progressively worse I believe, for a couple of months before they finally even sent the new boxes; in fact they seemed to only send those because the contract was switched to be in a new name, the previous person having moved out. That's more information than you wanted to read, I know, but the point is that it just *MIGHT* be your phone equipment, not the sky2 driver or Marvell or anything else in your computer.

---

