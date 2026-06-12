---
title: "Used swap increases continously until oom_killer disables everything"
date: 2011-08-02
forum: General Help
---

### Post by myqlarson on 2011-08-02
i'm getting ready to ditch Ubuntu. I fell in love with it more than a year ago, but the last few months have been painful.

Basically, I've never had any problems with Ubuntu (except for some minor sound driver issues), but as of a month or two ago, the whole system crashes quite regularly. As soon as the system starts using swap, it will never, ever go down. It keeps growing and growing until it's completely consumed and then the system dies. I can exit every program running, and it won't go down. 

I've installed Munin so that I can see when it's going to die. I have to save all of my files and reboot.

Nothing has really changed recently. No new programs, no new processes. I use it for some programming (NetBeans), web development (LAMP), word processing, internet, etc. Nothing too novel or unique. I'm current on all updates, kernel, etc. Whatever comes through the software updates from Ubuntu, I agree to.

Any ideas on what might be going on? I even tried someone's suggestion of turning swap off, then back on. But even with almost no programs running, I couldn't turn swap off because it claimed there wasn't enough memory available to move the swap to RAM....

Thanks for any tips!

---

### Post by wildmanne39 on 2011-08-03
Hi, maybe this link well help.
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

### Post by myqlarson on 2011-08-03
> **wildmanne39 said:**
> Hi, maybe this link well help.
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)


Thanks. Which particular part of the FAQ do you recommend? I've already read that several times over the past few weeks as I've tried to troubleshoot this on my own.

---

### Post by wildmanne39 on 2011-08-03
Hi, I would set the swapiness to 10 and see how that does.

---

### Post by myqlarson on 2011-08-04
> **wildmanne39 said:**
> Hi, I would set the swapiness to 10 and see how that does.

Thanks again for your suggestion, but the problem is not how often or to what degree the swap is being used. I have tried a range of values, from 1 to 80 with no difference. 

The problem is that once swap usage begins, it never goes down no matter what I do. 

There's clearly a memory leak somewhere and I have tried to track it down but have had no luck. I've looked through most other posts dealing with memory leaks and have tried to avoid programs suspected of such to no avail...

---

### Post by wildmanne39 on 2011-08-04
Hi, I am going to do some research on this.

How much memory do you have?

---

### Post by wildmanne39 on 2011-08-04
Hi, if you have not already done so type top in the terminal and watch it and see if you can find what is causing the problem.

---

### Post by myqlarson on 2011-08-22
it looks like the culprit is probably Compiz's known memory leak.

---

