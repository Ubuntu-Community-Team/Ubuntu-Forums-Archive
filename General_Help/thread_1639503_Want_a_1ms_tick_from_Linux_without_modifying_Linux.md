---
title: "Want a 1ms tick from Linux without modifying Linux Kernel"
date: 2010-12-06
forum: General Help
---

### Post by Like2Learn on 2010-12-06
I need to develop an embedded application running on Linux, to be more specific, Wind River Linux 4.0 is my favorite for now. My application requires a timer, or scheduler, which is required to tick my application for about every 1ms. I say "about" because there is no strict timing requirements, and either 1.01ms or 0.98ms would be acceptable. In my application, written in C++, I will implement OBSERVER pattern and Listener paradigm to get a full-featured scheduler to dispatch events to processes at variable rates, say 5ms, 10ms, etc. 
 
I would like to know if I can accomplish the above design without modifying the linux kernel, since under GPL, having a kernel module in my application will cause my application to be GPLed. At this moment I don't want to go that far yet. If there is something in the kernel already available, and can tick my application every 1ms, I would like to use it directly in my application. I hope this way will save me from the GPL license issue. Any thoughts? Thank you in advance!

---

### Post by efflandt on 2010-12-06
For timing you can use the rtc (real time clock).  It can generate interrupts anywhere from 2 Hz to 8192 Hz in increments of a factor of 2, although, only root can set it faster than 64 Hz.

You can web search "linux rtc" or here is one discussion [http://www.mjmwired.net/kernel/Documentation/rtc.txt](http://www.mjmwired.net/kernel/Documentation/rtc.txt)

---

