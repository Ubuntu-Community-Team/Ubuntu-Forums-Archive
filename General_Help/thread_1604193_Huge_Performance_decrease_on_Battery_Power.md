---
title: "Huge Performance decrease on Battery Power"
date: 2010-10-23
forum: General Help
---

### Post by synergie on 2010-10-23
Hi there,

I'm having a huge performance decrease when I'm on Battery Power. Plugged in this thing runs AMAZING, HDMI with HD video, I can run compiz 3d, full desktop advanced effects, HD video from youtube, you name it. Just when I pull the cable out it slows down. I tried disabling ATI powerplay but that didnt help.

Specs:
MSI Windu230L
ubuntu 10.10 64bit
dual boot iwndows 7 64 bit
AMD Athlon X2 64 Neo MV40
ATI Radeon HD
2 gig ram
4 gig swap (i plan on upgrading the ram)
250 gig hd (100 gig or so to ubuntu)

Is there a way I can toggle the performance, so that I can get "plugged in level performance" even when i'm on battery power? I'm not too bothered about how long the battery lasts. I'm usually always near an outlet.

---

### Post by synergie on 2010-10-23
The GPU        ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics

I ran a performance test and here is what I found:

On battery power the timed cache reads run at 315 MB/sec
On AC Power it runs at 700 Mb/sec

Under power management I have the "spin down hd" option unchecked while on battery power. Any suggestions?

---

### Post by synergie on 2010-10-23
Solved!!!! I love it when I figure these things out on my own:

My hypotheses:  It couldn't have been the GPU as I mucked with all the ATI Catalyst settings in every way.

I ran some benchmarking tests, the built in System Test Feature was amazing.  After doing some regression testing with various programs I isolated that it had something to do with power management on the chipset.  

I ran 

**cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor**

at first it came back with "on_demand"

Then, in my BIOS setup I disabled the AMD PowerNOW feature.

running the same command returned nothing.  My guess is that Ubuntu scales CPU performance based on power availability.  Personally I don't care to conserve... Rather have performance!

Needless to say I returned and this thing is fast as hell now.  I can play HD video seamlessly via HDMI or on the screen.

---

### Post by Rasa1111 on 2010-10-23
awesome!
Nice work! :D

---

