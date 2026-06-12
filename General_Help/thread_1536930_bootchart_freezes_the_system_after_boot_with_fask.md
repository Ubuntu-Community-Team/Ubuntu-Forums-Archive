---
title: "bootchart freezes the system after boot with fask"
date: 2010-07-22
forum: General Help
---

### Post by Chaconne on 2010-07-22
Hi, all,

I rebooted my PC this morning and a regular fsck came in during the boot. It was probably on my biggest partition so it took some time to finish. After I logged in, I noticed bootchart consumed 100% of one of my CPU cores(AMD 64 x2) and more than 3G of my memory(65%+ according to my conky).

It lasted for more than half an hour and finally the CPU load dropped, but memory consumption still high with almost 100% memory(4.6G+ in total) in use and more than 2G in swap(6G+ in total). All other programs were nearly hanged by bootchart because no memory could be used. I saw kswapd0 pocess in high CPU usage but it didn't help to free any memory.

Finally I killed bootchart and everything went normal. It was actually not the first time I killed bootchart because of its ridiculous resource usage but this time, I was almost angry about it.

I found there was a [bug report on the same phenomenon]("https://bugs.launchpad.net/ubuntu/+source/bootchart/+bug/218499"), but it was finally set to Won't Fix. Does anyone understand why this such critical problem is considered non-issue? As this would surely happen in the future, does anyone have some suggestion on how to prevent bootchart from running after a fsck boot?

Thanks in advance.

---

### Post by Nisuspi on 2010-07-28
Weird - had exactly the same problem this morning. First time in three years of using this system that I'm aware of, just after an upgrade to 10.4 too.

---

