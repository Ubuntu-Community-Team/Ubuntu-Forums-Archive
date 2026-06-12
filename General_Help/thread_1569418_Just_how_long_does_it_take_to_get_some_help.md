---
title: "Just how long does it take to get some help?"
date: 2010-09-06
forum: General Help
---

### Post by OoooBuntu on 2010-09-06
No, not in the forums... I'm talking about the computer I'm testing to possibly replace my old (what I thought was slow) 98SE box. 

Latest version 10.04.1, AMD 1.4Ghz, 512MB, installed on a 6GB HD.

Even with a brand-new, fresh install, booting to the main screen, clicking the Help icon or hitting F1 takes over a minute of disk activity before the first help screen finally finishes loading. Similar results getting help in programs or menus.
Much quicker the second time around, probably because everything's still lurking in memory.

The same machine with a test-install of XP Pro takes 4.5 seconds.
The "carved by cavemen" 98SE box takes less than 2 seconds.

Is this "normal" behavior?

......

Maybe later I'll ask about getting it to recognize the AGP card (have to use PCI), detecting the monitor, using ALL the resolutions of the PCI card and monitor (max 832x624 at the moment), or the seemingly impossible task of having it network with the 98SE machine (both plugged into the same Siemens DSL modem/router).

---

### Post by asmoore82 on 2010-09-06
I would be willing to bet that the machine in question has an
AMD "Duron" CPU, is this the case?

Linux doesn't get along well with low cache CPU's such as Celerons and Durons.

P.S. I just noticed the "6 GB" Drive - is that a typo?
A drive that is truly that small wouldn't work great with Linux either.
The small size is not the real problem, though, it's just that anything
that old would have very low cache and very slow seek time.

This issue wouldn't affect windoze as badly until fragmentation sets in.
See this explanation: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by jcolyn on 2010-09-06
A computer with those specs would be better off with puppy, peppermint, or crunchbang since these OS's don't use much hd space or ram..

You're asking too much of it with 10.04..

---

### Post by OoooBuntu on 2010-09-06
> I would be willing to bet that the machine in question has an
AMD "Duron" CPU, is this the case?Nope. Athlon XP1600+ on an Asus A7A266.

> P.S. I just noticed the "6 GB" Drive - is that a typo?Nope again. I keep some older drives around for testing.  XP is on another 6GB.
> it's just that anything that old would have very low cache and very slow seek time.Just seems odd that it takes that long to load a simple help menu. What's it doing... building the menus from 10,000 pieces scattered all over the drive, then recompiling the displaying program?

---

### Post by Forgotten Path on 2010-09-06
I'm not sure it has anything to do with his computer specs... I have the exact same problem, while everything else runs perfectly. See my signature for my box's specs.

---

### Post by clhsharky on 2010-09-06
OoooBuntu

> Is this "normal" behavior?
Yes, apples and oranges.

Compare modern OS like Lucid with Vista or 7.


Sharky

---

### Post by egalvan on 2010-09-06
> **OoooBuntu said:**
> Nope. Athlon XP1600+ on an Asus A7A266

capable chip; small cache, but capable.

> Nope again. I keep some older drives around for testing.  XP is on another 6GB.

very useful things, those 6g-20g drives... folks toss them out..cheap!

> Just seems odd that it takes that long to load a simple help menu. 
**What's it doing... building the menus from 10,000 pieces scattered all over the drive,** 
then recompiling the displaying program?

The first time it runs, yes it is doing some reading to assemble the info.
MS's help system is similar... you can choose to keep the help files compiled to save time, or compile at run to save space.
chm is the extension MS uses, IIRC (compiled help module)
Many pre-installed (OEM) systems come with the "speed" option already set, so MS won't "look" bad... ;)

The subsequent times should be in the sub-10 second range...
if not, you may have storage space issues...
try running 'htop' before doing the F1 thing... it will tell all.


I have an old Hardy install that shows F1 in under three seconds.
It's been running rock-solid since April 2008.

---

### Post by an0dos on 2010-09-06
You should try out lubuntu. Lxde works better than the default gnome on slower systems you may also want to try chromium instead of the default firefox. Firefox is becoming rather bloated.

---

