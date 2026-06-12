---
title: "UPS Suggestions?"
date: 2010-04-06
forum: General Help
---

### Post by kens8 on 2010-04-06
My electric has flickered far too many times over the last couple months, so I'm in the market for a relatively cheap UPS.  I want to make sure I get one that will shut down ubuntu if the power goes out completely, though.  Any suggestions?  Thanks!

---

### Post by duanedesign on 2010-04-06
Good question. For Linux I have always heard good things about APC Smart-UPS used with apcupsd.

---

### Post by quadproc on 2010-04-06
> **kens8 said:**
> My electric has flickered far too many times over the last couple months, so I'm in the market for a relatively cheap UPS.  I want to make sure I get one that will shut down ubuntu if the power goes out completely, though.  Any suggestions?  Thanks!
Your reply is remarkably timely - we had a severe power crash here yesterday and that got me to researching UPS products today.  I was lucky - I had shut down this system about 10 minutes before the power outage.

I can tell you what I decided, and why.  Of course, your requirements may be different than mine so this might not be useful to you, but here goes:

I selected the APC RS series because it had very few negatives in the reviews that I read, and it had one huge positive: according to their claims, the_ APC software supports Linux_!  It uses a USB connection to communicate with the computer.  I do not yet have one of these UPS's in house to see how it actually works, but I should have one soon.

They offer them in several different capacities.  I suggest actually measuring your system's power usage before you select a size, and be aware that the wattage they can produce is only about 60% of the VA (volt-amperes) that they are rated for.

BTW, Ubuntu 9.10 seems to be pretty rough around the edges in terms of Suspend and Hibernate - it took many minutes for this system to close down.  Hopefully that will be improved in the future.

quadproc

---

### Post by jessel on 2010-05-11
quadproc:

Hey, I was wondering what you ended up purchasing and how it worked out.  My old APS unit died a while back and I really need to replace it. I'm considering getting something similar (800VA) but getting a unit with the usb interface.

---

### Post by quadproc on 2010-05-13
> **jessel said:**
> quadproc:

Hey, I was wondering what you ended up purchasing and how it worked out.  My old APS unit died a while back and I really need to replace it. I'm considering getting something similar (800VA) but getting a unit with the usb interface.

This is a long delayed response but here it is:

I found an APC MODEL : Back-UPS BX1500G at a local store.  It is rated at 1500 VA and about 800 watts.  Since the main computer has an 850 watt power supply I figured that that was a pretty good match; I have a couple of monitors plugged into the UPS as well as the computer but the computer is not fully loaded so I have enough head room.

One big disappointment: APC [COLOR=Red]does not[/COLOR] support Linux themselves contrary to their literature.  However, you can get apcupsd for free and it works well.

So far the UPS has been flawless.  I do note one thing of interest: when the UPS is running from its battery it makes a buzzing noise similar to a noisy fluorescent light.  The noise isn't very loud and it is not a problem, I was just surprised.

quadproc

---

### Post by jessel on 2010-05-14
Thanks for following up. I'm yet to buy anything myself.

---

