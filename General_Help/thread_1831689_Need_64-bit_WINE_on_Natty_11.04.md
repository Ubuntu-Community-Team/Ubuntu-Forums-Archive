---
title: "Need 64-bit WINE on Natty 11.04"
date: 2011-08-23
forum: General Help
---

### Post by Ievoigh0 on 2011-08-23
I don't usually have troubles I can't solve alone or at least search through here to find a solution. This is NOT one of those times.

I have Natty 11.04 on a 64-bit machine. I have 32-bit WINE. I need 64-bit WINE. I tried following wiki.winehq.org/Wine64 but I run into probs at the end of the GCC installer script, then in the next bit it tells me 11.04 isn't supported. I don't want to roll back to 10.10

Is there already a solution I can't find, is this just me, or is there no answer?

---

### Post by loolooyyyy on 2011-08-23
> **yonatan703 said:**
> I don't usually have troubles I can't solve alone or at least search through here to find a solution. This is NOT one of those times.

I have Natty 11.04 on a 64-bit machine. I have 32-bit WINE. I need 64-bit WINE. I tried following wiki.winehq.org/Wine64 but I run into probs at the end of the GCC installer script, then in the next bit it tells me 11.04 isn't supported. I don't want to roll back to 10.10

Is there already a solution I can't find, is this just me, or is there no answer?

why dont you try this? : forget about wiki at wine and install it through repositories!
it'll downloads the proper 64bit version by itself
you also have the option of using 32bit Natty
since you say you can manage everything, i think i didn't get part of what you are saying, can you explain more?

---

### Post by Ievoigh0 on 2011-08-24
> **loolooyyyy said:**
> why dont you try this? : forget about wiki at wine and install it through repositories!
it'll downloads the proper 64bit version by itself
you also have the option of using 32bit Natty
since you say you can manage everything, i think i didn't get part of what you are saying, can you explain more?

I didn't say I can manage EVERYTHING. In fact, I said this is one of those times I admit to being lost. I got the 32-bit from the repository. I can't find a 64-bit, thus I am here. Can you suggest a repository that perhaps I have overlooked?

---

### Post by jwbrase on 2011-08-25
Is there a particular bit of Windows software you need to run that actually needs 64-bit?  As I understand, practically all Windows software has a 32-bit version, much of it is *only* available in 32-bit, and Wine64 at the moment is rather buggy and not yet ready for general use (see [http://wiki.winehq.org/Wine64ForPackagers](http://wiki.winehq.org/Wine64ForPackagers)), and Wine32 should run perfectly well on 64-bit Linux, so unless you have a specific 64-bit-only Windows software package you want to run, it would almost certainly be better to stick with Wine32.

---

### Post by Ievoigh0 on 2011-08-25
What I have comes to me ONLY in 64-bit.

---

### Post by Ievoigh0 on 2011-08-25
Just followed the link you provided, which led me elsewhere... Long and short, I see we can expect 1.4 with 64-bit due out sometime within the next 4.5 months. I think I can wait, maybe.

---

### Post by jwbrase on 2011-08-25
> **yonatan703 said:**
> Trying to install AutoCAD, and I only have the 64-bit installer.

How did you get ahold of it? Is this a CD? Is it the trial version they have available for download on their website?

---

### Post by loolooyyyy on 2011-08-25
i'm really confused too, it's supposed to be in repositories?!
and totally forget about compiling it, because it IS already compiled and ready for you
i'll give you my 'sources' file when i get home
something else: the machine is 64, but is Natty's installation too?

---

