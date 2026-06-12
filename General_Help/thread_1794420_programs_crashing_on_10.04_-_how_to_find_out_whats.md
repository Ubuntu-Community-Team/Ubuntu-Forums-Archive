---
title: "programs crashing on 10.04 - how to find out whats the problem"
date: 2011-07-01
forum: General Help
---

### Post by arvsr1988 on 2011-07-01
Programs are crashing on my ubuntu 10.04 system - I don't know whether its a hardware problem or a problem with the OS - is there a way to check that? 

I've run memtest (version 4.00) and I'm getting quite a few errors - the error bits output reads 02000000 for all of the errors. 

Is there any way that I can find out whether this is an OS problem or a hardware problem?

---

### Post by wildmanne39 on 2011-07-01
> **arvsr1988 said:**
> Programs are crashing on my ubuntu 10.04 system - I don't know whether its a hardware problem or a problem with the OS - is there a way to check that? 

I've run memtest (version 4.00) and I'm getting quite a few errors - the error bits output reads 02000000 for all of the errors. 

Is there any way that I can find out whether this is an OS problem or a hardware problem?
Hi, I think the memory test is your answer, sounds like you need to get new memory. Also the program you are trying to run, start it from a terminal that way when it crashes you will have the errors in the terminal of why it crashed.

---

### Post by arvsr1988 on 2011-07-01
I've got two RAM cards - when i tested with both together, there were 1000's of errors - then i took one of them off and the memtest gives me some 20 errors - but both of the err-bit outputs were the same.  Does that mean that there is some other problem in the motherboard/etc or are both the RAM cards dead?

---

### Post by wildmanne39 on 2011-07-01
> **arvsr1988 said:**
> I've got two RAM cards - when i tested with both together, there were 1000's of errors - then i took one of them off and the memtest gives me some 20 errors - but both of the err-bit outputs were the same.  Does that mean that there is some other problem in the motherboard/etc or are both the RAM cards dead?Hi, I am not sure, but it does not sound good the only time I have heard of error messages with ram is when they are bad, or incompatible. Hopefully someone with more experience with ram issues will pop in and give some advice. Are both of your memory the same brand and speed?

---

### Post by FormatSeize on 2011-07-01
> **arvsr1988 said:**
> Does that mean that there is some other problem in the motherboard/etc or are both the RAM cards dead?
It's more likely the RAM than the motherboard. When something with the motherboard happens, much more dreadful things than memory test errors and program crashes start happening. Devices stop working and your computer only boots when it feels like it, then stops booting on the day you need it most. I had this happen to me a couple months ago.

---

