---
title: "Ubuntu CPU/FSB Overides"
date: 2009-12-15
forum: General Help
---

### Post by mxmike51 on 2009-12-15
Hi, :popcorn:

I just built a new windows free asus p5kpl rig. I purchased 1066 Mhz memory to take advantage of the mobo overclock ability. I set my FSB from 200 to 267 Mhz to bump the mem from 800 to 1068 Mhz. My processor is a 2.2 Ghz dual core celeron E1500. With the FSB at 267 Mhz  my processor max should be 2937 Mhz. CPU Frequency Scaling Monitor is showing my cpu at 1200 Mhz or 2200Mhz. Using the speed step! very cool!

Is 1.2 or 2.2 Ghz my cpu actual speed? or is it actually higher due to the FSB OC?

I guess my main concern is.. Does Ubuntu 9.10 over ride my FSB settings in the BIOS?

Is it setting my Host Clock at 200 Mhz which would set my Front Side Bus at 800?

That is the recommended FSB for the E1500 CPU as well

If it is then my 1066 memory is running at 800 Mhz.

I think it is just using the speed step technology which only controls the processor. But it makes me wonder because with the FSB Over Clock my processor should still be Over Clocked as well and the CPU Frequency Scaling Monitor is not indicating that.

Also, is there an application like cpu-z for linux?

Thanks in advance!

Mike

---

### Post by mxmike51 on 2009-12-15
:D

I think I found what I was looking for  ;)  dmidecode -d /dev/mem

Gives me all the info cpu-z and then some.

My processors actual speed is 2948 Mhz and my memory is at 1068! :KS

Very Cool!

Now i'm going to remove the CPU Applet which is very cool but I don't need to continuously monitor my CPU.

I also see that I could have opted for 1200 MHz Memory and played with the processor multiplier and got the front side bus up to 400 MHz. Something to think about for next time. This one is very fast as is!

---

