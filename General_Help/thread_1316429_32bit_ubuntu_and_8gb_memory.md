---
title: "32bit ubuntu and 8gb memory"
date: 2009-11-05
forum: General Help
---

### Post by dsbig123 on 2009-11-05
I used to have 64bit windows on my machine and switch over to ubuntu but becuase of problems I was  having with flash in the 64bit ubuntu I decided to use the 32bit instead and I know the memory limits on 32bit but I noticed in system monitor it still showing I have 8gb memory, actually says 388.4 mib (4.8%) of 7.9gb

so does ubuntu 32bit still have memory limits?

---

### Post by Roasted on 2009-11-05
To my knowledge, it doesn't matter what OS it is, as long as it's 32 bit, it can only see 3.5ish GB of RAM. I have no idea why 32 bit Ubuntu would see 7.9 GB of RAM like you're saying...

It's an architecture limit based on the design of 32 bit chips. Not an OS limitation.

---

### Post by dcstar on 2009-11-06
> **Roasted said:**
> To my knowledge, it doesn't matter what OS it is, as long as it's 32 bit, it can only see 3.5ish GB of RAM. I have no idea why 32 bit Ubuntu would see 7.9 GB of RAM like you're saying...

It's an architecture limit based on the design of 32 bit chips. Not an OS limitation.

32-bit kernels with PAE enabled can see as much RAM as you have, the issue is that the maximum any single 32-bit process can access is 4GB, and processes running in one section of RAM may not have direct access to other processes running in another section.

The bottom-line still is that using a 32-bit O/S on a machine with more than 4GB RAM makes the extra RAM pretty pointless.

As far as the OP goes, I have been successfully using the Adobe 64-bit Flash plugin for a long time now on 64-bit Ubuntu, as thousands of other also have.

---

### Post by Uncle Spellbinder on 2009-11-06
> **dcstar said:**
> ...As far as the OP goes, I have been successfully using the Adobe 64-bit Flash plugin for a long time now on 64-bit Ubuntu, as thousands of other also have.

On Karmic? With 'desktop effects' enabled? Many others are having horrible issues with Flash (32 or 64 bit versions) when using Karmic and 'desktop effects' enabled.

---

### Post by dcstar on 2009-11-06
> **Uncle Spellbinder said:**
> On Karmic? With 'desktop effects' enabled? Many others are having horrible issues with Flash (32 or 64 bit versions) when using Karmic and 'desktop effects' enabled.

No, as my profile says I use 9.04. You really have to be quite foolish to jump onto a new release and expect everything to be working correctly - people who want full functionality should wait a month or so (at least) for things to get sorted out.

As someone who has been using Ubuntu since 2004, you learn when to upgrade and the times to leave things as they are.

---

### Post by Uncle Spellbinder on 2009-11-06
> **dcstar said:**
> No, as my profile says I use 9.04. You really have to be quite foolish to jump onto a new release and expect everything to be working correctly - people who want full functionality should wait a month or so (at least) for things to get sorted out.

As someone who has been using Ubuntu since 2004, you learn when to upgrade and the times to leave things as they are.


As an Ubuntu user since 2004 myself, I love to delve in to the newest as it becomes available. And no, that's not "foolish". Quite insulting to be called "foolish", actually.

As far as the Flash issue, I'm not complaining myself,  was just pointing out that there are many with these flash/64 bit issues on Karmic.

---

