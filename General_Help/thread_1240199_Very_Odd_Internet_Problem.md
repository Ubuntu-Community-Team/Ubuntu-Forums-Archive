---
title: "Very Odd Internet Problem"
date: 2009-08-14
forum: General Help
---

### Post by Valok on 2009-08-14
So over the past 2 weeks or so I've been trying to install various different distros on my computer after deciding I really wanted to go back to linux.

First, I tried arch, but couldn't get the internet working so I scrapped that.

Next, I tried Kubuntu 9.04, but couldn't get the internet working their either.

This morning I tried Ubuntu 9.04, and still the same problem.

I put windows back on my computer to make sure that it wasn't a hardware problem, and I indeed could access the internet there.  Then, out of desperation, I installed Ubuntu 8.04 which is the last linux distro I had on my computer that worked.  And guess what, it still works!

Since I obviously don't want to be stuck with older versions of Ubuntu and other distros, I want to figure out the problem.  But I'm not sure what it could be.

What do Arch, (K)Ubuntu 9.04 have in common that Ubuntu 8.04 does not?

I'd really appreciate any input on the matter because I've been butting my head against a brick wall for 2 weeks, and I just want to figure it out already.  Thank you!

---

### Post by P4man on 2009-08-14
Arch and ubuntu 9.04 both have a newer kernel than 8.10.

I suppose you are having problems with a wired ethernet connection ?
Can you post the output of lspci here ?

---

### Post by Valok on 2009-08-14
Sorry, you are right in that the problem is with a wired connection.  I'm not at home at the moment, but you want the lspci output when the computer is running 8.04 (which works) or 9.04 (which doesn't).

What specific info are you looking for?  I might have some of that handy.

---

### Post by P4man on 2009-08-14
just want to know what network card you have. 8.04 can tell you that too.

are you behind a router or using pppoe or something? just want to find out what it is that broke on 9.04.

---

### Post by Valok on 2009-08-14
My ethernet card is 

```
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
```

And I am connecting using a router in both 8.04 and 9.04

---

### Post by P4man on 2009-08-14
I remember seeing a lot of ppl with problems with the nvidia onboard lan. IIRC, most got it solved by disabling the built in firewall (in the bios).

give it a shot and boot the live cd and see if it helps. If that doesnt work, we can look further.

---

### Post by Valok on 2009-08-14
Thanks!  I'll give that a try once I get home and report back.  

Thanks again!

---

### Post by Bucky Ball on 2009-08-14
> **P4man said:**
> Arch and ubuntu 9.04 both have a newer kernel than 8.10.



Exactly. I wouldn't worry too much about being out of date with 8.04. It is very stable (if that is what you are after) and fully supported for a few years yet so still very much current. :)

You may well find that if you try 9.04 in a week or a month your problem might be fixed.

8.04 LTS (Long Term Support)

---

### Post by Valok on 2009-08-14
Yeah I'm really hoping that (if I can't get it to work) then 9.10 which I think is coming this fall will work better.

---

