---
title: "Benchmarking via WINE"
date: 2010-03-12
forum: General Help
---

### Post by rcayea on 2010-03-12
I am wondering if I install some benchmarking utilities via WINE, should I expect inaccurate results?

I know about other benchmarking apps such as phoronix, but there are so many more I want to use that are of the .exe nature. 

Any tips is appreciated.

---

### Post by rcayea on 2010-03-12
bump

---

### Post by Mark Phelps on 2010-03-13
> **rcayea said:**
> I am wondering if I install some benchmarking utilities via WINE, should I expect inaccurate results?

Guess it depends on what you mean by "innacurate" -- and why you're doing the benchmarking in the first place.

If you're comparing the runtime performance of MS Windows apps in Ubuntu to what the same apps take (on the same hardware) in MS Windows, my guess would be that your benchmark results in Wine would be fairly accurate because, unlike in a virtual machine, you're not running in a separate environment.

Don't use Wine myself, but I have seen reports of folks saying that some MS Windows apps run faster in Wine than on a comparably equipped MS Windows box.

---

### Post by rcayea on 2010-03-13
Thanks for taking the time to reply. 

I don't have any Windows OSs installed on any of my three hard drives so I don't plan on comparing results.

I simply am into trying to overclock my cpu and as stated I don't have any MS OSs installed that I can turn to, to try and get some benchmarks before I do any other tinkering. 

Has anyone had success with WINE and benchmarks? (meaning-do you think they were fairly productive results that you might end up getting as if you were running an MS OS).

---

### Post by LoneWolfJack on 2010-03-13
WINE re-implements windows on linux with available linux libraries. thus, WINE should not be slower than windows, but you still may get totally different results.

however, if you are just trying to compare your CPU performance before/after overclocking, you will mainly be interested in the relative numbers, for which WINE will do fine.

---

