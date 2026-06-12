---
title: "Ubuntu sudden logouts and goes to command line screen"
date: 2010-05-09
forum: General Help
---

### Post by kako13 on 2010-05-09
Hi,

My problem is that Ubuntu suddenly logout after a while (~15 min).  

I took a photo to my monitor which show some lines in red. 

Probably to post some of the logs made by Ubuntu.  However, I do not know which one.

I am using Ubuntu 10.04 upgraded from Ubuntu 9.10.

---

### Post by kako13 on 2010-05-09
I ran memtest87 but I am not sure about the results.  I had attached an screenshoot.

Any suggestion? :(

---

### Post by kako13 on 2010-05-10
Any suggestion would be really appreciate!

---

### Post by kako13 on 2010-05-11
Bump...

---

### Post by GSF1200S on 2010-05-11
I would be interested to see if anyone has any ideas on this. Looking at your memtest results, it seems like you have a slew of errors :confused: Ive never really used memtest, but im running it on my netbook as we speak (netbook works perfect, so memtest should come through with a pass).

The only thing I can think of is, are you overclocking at all? Often times if you up the base clock then your DRAM frequency will rise too, and this can cause issues. In my experience, RAM is much more sensitive to being overclocked than a (good) cpu is. 

If you arent overclocking, do you have some spare ram to throw in the computer as a test?

Once again, I dont know much, but hopefully we can figure out whats wrong because it would be good for both of us to know..

---

### Post by kako13 on 2010-05-11
Yep is look like the memory is not working properly.

I did a test an remove one of the four memories and my system seem to be working properly.

I am going to run the test again with 3 memories to see what happen.

> **GSF1200S said:**
> I would be interested to see if anyone has any ideas on this. Looking at your memtest results, it seems like you have a slew of errors :confused: Ive never really used memtest, but im running it on my netbook as we speak (netbook works perfect, so memtest should come through with a pass).

The only thing I can think of is, are you overclocking at all? Often times if you up the base clock then your DRAM frequency will rise too, and this can cause issues. In my experience, RAM is much more sensitive to being overclocked than a (good) cpu is. 

If you arent overclocking, do you have some spare ram to throw in the computer as a test?

Once again, I dont know much, but hopefully we can figure out whats wrong because it would be good for both of us to know..

---

### Post by kako13 on 2010-05-11
Yep is look like the memory is not working properly.

I did a test and remove one of the four memories and my system seem to be working properly.

I am going to run the test again with 3 memories to see what happen.

> **GSF1200S said:**
> I would be interested to see if anyone has any ideas on this. Looking at your memtest results, it seems like you have a slew of errors :confused: Ive never really used memtest, but im running it on my netbook as we speak (netbook works perfect, so memtest should come through with a pass).

The only thing I can think of is, are you overclocking at all? Often times if you up the base clock then your DRAM frequency will rise too, and this can cause issues. In my experience, RAM is much more sensitive to being overclocked than a (good) cpu is. 

If you arent overclocking, do you have some spare ram to throw in the computer as a test?

Once again, I dont know much, but hopefully we can figure out whats wrong because it would be good for both of us to know..

---

### Post by mgranet on 2010-05-11
Your system appears to have DDR1 ram, but it looks to be clocked at 340MHz. DDR400, the fastest DDR1, clocks at ~200MHz. The 150% overclocking alone is enough to cause problems. Also, it is running in single channel mode, which is killing your system performance. I would try resetting the BIOS to defaults. Pulling a stick might cause the symptom to go away, but the root cause is still there.

---

### Post by kako13 on 2010-05-11
> **mgranet said:**
> Your system appears to have DDR1 ram, but it looks to be clocked at 340MHz. DDR400, the fastest DDR1, clocks at ~200MHz. The 150% overclocking alone is enough to cause problems. Also, it is running in single channel mode, which is killing your system performance. I would try resetting the BIOS to defaults. Pulling a stick might cause the symptom to go away, but the root cause is still there.

For some reason memtest86 read them as DDR1 when actually they are DDR2(Kingston 4GB, (2x1GB) DDR2 667, DIMM (PC2 5300) 667MHz).  Also, the BIOS POST said Dual Channel.

If you have any other suggestion, please let me know.

---

