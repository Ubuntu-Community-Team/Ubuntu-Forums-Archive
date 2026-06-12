---
title: "&quot;Encrypt Home Directory&quot; option leads to slow file access"
date: 2012-07-16
forum: General Help
---

### Post by Tarfeather on 2012-07-16
Summary: It seems that accessing lots of files(in the order of magnitude of 100000) will be around 50 times slower with encryption than without. I'm really curious why that is.

How I came to that conclusion: I've recently started working on the firefox source code with hg. hg stores the history for each file in a separate file in the .hg/ directory, which for mozilla make up several thousand files. I unpacked mozilla into my encrypted home directory, and noticed that hg actions which should usually take 10 seconds took 10 minutes for me. I read somewhere that these actions need to access many of the files in the .hg/ directory, but that in itself didn't explain why it was taking 50x longer for me than for others.

Moving mozilla into a non-encrypted directory fixed this. hg qpop sped up from 10 minutes to 10 seconds time consumption. I can only conclude that encryption slows down file lookup a lot, and that this becomes notable only when you have many many small files which you want to access in short order.

Any ideas *why* this happens? Any fixes?

---

