---
title: "cat /proc/cpuinfo displaying wrong info"
date: 2010-02-17
forum: General Help
---

### Post by ketan_shah_2008 on 2010-02-17
Hey guys,

I recently built a new computer.  For CPU, I am using AMD Athlon II X2 @ 2.8GHz...  However, when I do cat /proc/cpuinfo, I get the following:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 6
model name      : AMD Athlon(tm) II X2 240 Processor
stepping        : 2
cpu MHz         : 800.000
cache size      : 1024 KB

and same thing for processor: 1

Notice that for cpu MHz, it says 800.000.  However, that is not correct... Shouldn't it say 2800???

Is this a bug?  Am I looking at this wrong?

A little insight would be appreciated.  Thanks.


-Ketan

---

### Post by squaregoldfish on 2010-02-17
The output of cpuinfo gives the current speed of the processor.

If your machine isn't doing much, the cpu will scale back the processor speed to save power. If you run something processor-intensive and look at cpuinfo again, you should see the number change - I've just done it on my machine to be sure.

Steve.

---

### Post by ketan_shah_2008 on 2010-02-17
Steve,

Thank you for your response.  That makes sense.  I will try to do something to intensify the CPU and then look at it again.  Thanks again...

-Ketan

---

