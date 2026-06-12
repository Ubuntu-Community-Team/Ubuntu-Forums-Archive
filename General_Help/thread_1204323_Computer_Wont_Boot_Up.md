---
title: "Computer Wont Boot Up"
date: 2009-07-04
forum: General Help
---

### Post by iheartubuntu on 2009-07-04
Let me preface this by saying I had this problem a year ago when the computer was a Windoze XP system. I am now experiencing the same problem with the desktop system that has been an Ubuntu system for a year already.

So this is NOT an Ubuntu issue, but I am hoping someone here has experienced this or can direct me to what might be wrong with my system.

This computer is/was top of the line 4 years ago. Its a Pentium 4 - 3.40ghtz system with 4GB of memory. Ubuntu shows it has dual core, but I didnt realize there were dual cores with such high ghtz 4 years ago. But what do I know. Anyways, when it was still an XP system over a year ago, it started having this problem. When I turn the system ON, nothing happens. I get the first bios page (press F2) and then it hangs. I never get into any other screens. Putting an Ubuntu disc in a drive doesnt help as the computer doesnt get that far. I figured it might be an XP problem, so I wiped it and decided to go full on Ubuntu (I think 8.04 at the time). I have not had ONE problem with this computer until a couple days ago. Same prob... I turn it on and the computer hangs on me. I dont even get to the Ubuntu booting up page. What usually helps fixing the problem (albeit temporarily) I will just keep turning the power off and on until it gets past the bios screen. Or if I leave the computer off a day or two and come back to it, it will turn on fine.

So, this isnt an OS problem... I dont know what could be the prob so I am asking anyone for help. Could it be a RAM or CPU problem? A power supply problem? Any help would be appreciated! Thanks!

---

### Post by sdlynx on 2009-07-04
Can you get past the BIOS at all?

---

### Post by iheartubuntu on 2009-07-04
> **sdlynx said:**
> Can you get past the BIOS at all?

When Im having this problem, I cant even get into the BIOS!

---

### Post by moster on 2009-07-04
If that working OK before and without any of your reconfigurnig bios or adding new hardware you got this problem, then I would say it is serious problem.

You are lucky if it only power supply gone. Check that first, if it is not that, you are out of luck. It could be anything from cpu, motherboard, memory...

edit:
with check "power supply" I mean replace power supply inside computer with one that work for sure.

edit2:
if your computer is beeping, check you motherboard manual for that. Different sounds have different meanings.

---

### Post by sdlynx on 2009-07-04
> **shirteesdotnet said:**
> When Im having this problem, I cant even get into the BIOS!

Hmm if you can't even get that far I don't know what to do to fix this (I'm not really a hardware person).  It must be hardware error though.

---

### Post by iheartubuntu on 2009-07-07
Like I was saying, ever since I had switched to Ubuntu on this system, I havent had any problems until now. I just tried downloading some updates and the computer froze on me. I decided to press the power button to reset. Afterwards, the computer basically hung again, not letting me get into BIOS or anything.

Any thoughts on this?

I usually keep up to date on my Ubuntu updates, so Im looking at whats available now...

I dont see anything out of the norm... pidgin, some pulseaudio stuff, and xorg-video-intel.... strange though I have ATI, not intel.

---

### Post by moster on 2009-07-07
No Ubuntu or windows cannot do that. Computer ALWAYS must be able to get to the BIOS even if there is no OS installed. You are looking for solution in wrong place. You have some serious problem and it is not ubuntu update.

---

### Post by 3rdalbum on 2009-07-07
I had a similar problem when building a new computer. I moved the RAM to another slot and the problem hasn't appeared since.

As you've got 4 gigabytes of RAM in there, I'm assuming that all your slots are filled. Try taking out one pair and giving that a whirl. You probably have two RAM slots that are black and two that are another colour - take out the sticks from the black slots first, and if that doesn't help try putting them back in and taking out the RAM from the other two slots.

Your computer is probably not a dual-core. The later P4s were "hyperthreaded" - they pretend to have two cores so they can have two threads assigned to them. If they are stuck waiting for data to arrive to the first thread, they can switch to the second thread. Gives a modest speed boost. The new Core i7 processors and the Intel Atoms do the same trick.

---

### Post by iheartubuntu on 2009-07-07
> **3rdalbum said:**
> I had a similar problem when building a new computer. I moved the RAM to another slot and the problem hasn't appeared since.

As you've got 4 gigabytes of RAM in there, I'm assuming that all your slots are filled. Try taking out one pair and giving that a whirl. You probably have two RAM slots that are black and two that are another colour - take out the sticks from the black slots first, and if that doesn't help try putting them back in and taking out the RAM from the other two slots.

Your computer is probably not a dual-core. The later P4s were "hyperthreaded" - they pretend to have two cores so they can have two threads assigned to them. If they are stuck waiting for data to arrive to the first thread, they can switch to the second thread. Gives a modest speed boost. The new Core i7 processors and the Intel Atoms do the same trick.

Thanks for the info... It is hyperthreaded technology so that explains why Ubuntu sees dual core.

I'll try moving the ram around and see if it helps. I once had a problem with a new laptop a year ago and I just moved the ram around and no problems on that since. Thanks for the reminder! Sometimes I get stuck in one line of thinking and simple things like moving the ram around dont even enter my mind.

---

### Post by iheartubuntu on 2009-07-08
Well, last night I moved my ram chips around, rebooted, no probs. I installed all updates and the computer didnt hang on me. I rebooted again, no prob. I always get this too when I have to press and hold down the reset/power button to reset. Thats always when the system will hang on me. Not this time. Booted right up. Maybe tonight I will run a mem test to see if I find anything.

---

