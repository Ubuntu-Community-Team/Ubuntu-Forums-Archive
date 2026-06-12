---
title: "Can defective memory cause ubuntu to lock up?"
date: 2009-08-10
forum: General Help
---

### Post by rold50 on 2009-08-10
For the past two days, ubuntu locks up on me randomly (can't move mouse, keyboard and have to do hard reset).

When I checked my memory using memtest86, it found 100+ errors.

---

### Post by Wim Sturkenboom on 2009-08-10
Yes. At the moment that it accesses that part of the memory, you're in trouble.

---

### Post by rold50 on 2009-08-10
Thanks. If memtest found errors, does that mean for sure that the memory is defective?

In the first few tests, it didn't find errors, only at the later tests (don't remember if it was 5 or 6).

---

### Post by martinbaselier on 2009-08-10
When there are errors, you can be pretty sure it's the memory. It could in theory also be your motherboard. If the connection is broken it doesn't matter where, for the sytem to stop working. But most often it's the memory. That it doesn't show up at first, only means that the memory becomes less stable when the machine is on for some time.

---

### Post by bobince on 2009-08-10
> **rold50 said:**
> Thanks. If memtest found errors, does that mean for sure that the memory is defective?

Either it's defective, or it's running faster than its rated speed/latency. Worth a quick check in the BIOS to make sure you've not got some kind of overclock going on. Sometimes underclocking can make duff memory work OK, but in general if memtest has even a single error at the given (default SPD) speed for a memory stick, it needs replacing.

---

### Post by rold50 on 2009-08-10
Thanks. I'll try to isolate and figure out which of my memory stick is defective and see if that solves my lock-up problems.

---

### Post by lswb on 2009-08-10
Agree with above and also add, if you have more than 1 memory module, for example two 512MB SIMMS, you can try removing one at a time to see which is defective.

---

### Post by Wim Sturkenboom on 2009-08-11
In my opinion, a faulty memory test does not necessarily mean the the memory is faulty. Any of the components that is used in the test (processor, motherboard (as mentioned earlier), memory) can be faulty.

The steps
processor writes data to memory (via mobo)
processor reads data back from meory (through mobo)
processor compares data

In its simplest scenario
1)
if processor has a failure on its databus, the data that is written is corrupted at the moment that it leaves the processor, so compare will fail
2)
if mobo has a failure, the data that is written is corrupted by the mobo, so the compare will fail
3)
if the memory has a failure, the data is corrupted in the memory so the compare will fail

However, as your lockups don't start immediately and not all tests fail, number 3 is the more likely culpritt.

---

### Post by zkriesse on 2009-08-11
YES.....it sucks but yes, defective memory can cause MAJOR ISSUES!!!! BEWARE OF DEFECTIVE MEM!

---

### Post by Barafu Albino Cheetah on 2009-08-11
One guy asked me to repair his PC. memtest shows several errors, but the problem was that his memory chips were designed for higer-then-standart voltage of 2.1.  So check the info on your chips.

---

### Post by martinbaselier on 2009-08-11
@wim: 

You are right of course. But most often it's the memory. When this is not the case, it's probably the motherboard. A defect cpu happens the least often. I've worked a couple of years on a helpdesk for a hardware manufacturer. That gives you a pretty good impression of which parts have defects more often.

---

### Post by Wim Sturkenboom on 2009-08-12
> **martinbaselier said:**
> You are right of course.Of course :D

> **martinbaselier said:**
> But most often it's the memory. When this is not the case, it's probably the motherboard. A defect cpu happens the least often. I've worked a couple of years on a helpdesk for a hardware manufacturer. That gives you a pretty good impression of which parts have defects more often.I do not have your practical experience, so can not really judge. It's just a warning to people who experience memtest errors that replacing the memory might not solve the issue.

As I stated, the behaviour of the box and the memtest results indicate that it's more than likely the memory.

---

### Post by rold50 on 2009-08-14
Thanks. I removed the faulty memory and I haven't had a lock up since.

---

