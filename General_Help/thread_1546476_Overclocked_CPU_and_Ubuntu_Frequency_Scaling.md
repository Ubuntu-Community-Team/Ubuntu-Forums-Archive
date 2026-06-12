---
title: "Overclocked CPU and Ubuntu Frequency Scaling"
date: 2010-08-05
forum: General Help
---

### Post by cj.surrusco on 2010-08-05
I have a 2.9ghz AMD Athlon II X4, which I have overclocked to 3.65ghz. I know that Ubuntu automatically changes the frequency of the processor to save power, which I like, but it does not show my overclocked frequency. The highest that the frequency scaling will go is the stock clock, at 2.9ghz.

Is my processor actually reaching my overclocked speed? 

Thanks in advance.

---

### Post by What Rights on 2010-08-05
This is actually a good question. I would have to say no, but I maybe wrong. Have you got a program that tells you the current Mhz of your processor? I would look there.

---

### Post by DeMus on 2010-08-05
No, it won't. I have the same problem so I disabled Speedstep in BIOS and run on full power all the time, if I need it or not.
With Speedstep I also just reach the nominal frequency of the processor, which in my case is 2.4GHz, not the 3GHz overclocked value.
Also I am experiencing problems with Speedstep switched on, the frequency does not go up enough to let me do what I want to do. Especially watching video is a crime that way, it's like watching a slide show. No more Speedstep for me.

---

### Post by cj.surrusco on 2010-08-05
> **What Rights said:**
> This is actually a good question. I would have to say no, but I maybe wrong. Have you got a program that tells you the current Mhz of your processor? I would look there.
Thanks for the reply.

Well, I have System Stability tester, which actually shows my overclocked speed, but it will even show that speed if I set all of the cores to run at 800mhz with that frequency scaling monitor.

> **DeMus said:**
> No, it won't. I have the same problem so I disabled Speedstep in BIOS and run on full power all the time, if I need it or not.
With Speedstep I also just reach the nominal frequency of the processor, which in my case is 2.4GHz, not the 3GHz overclocked value.
Also I am experiencing problems with Speedstep switched on, the frequency does not go up enough to let me do what I want to do. Especially watching video is a crime that way, it's like watching a slide show. No more Speedstep for me.
Hi, thanks for the reply, but I'm not sure that I understand you correctly. I don't have speedstep on my motherboard. I just need to know if the Ubuntu frequency scaling will actually bring my CPU back to stock speed.

---

### Post by cj.surrusco on 2010-09-05
After doing some more research on this subject with benchmarks, I've found that frequency scaling works on a percentage basis. So when it says it's running at 2.9ghz (stock clock), it's running at 3.5ghz (O/C clock), and when it says it's running at 2.2 ghz, it's actually running at about 2.7ghz.

---

