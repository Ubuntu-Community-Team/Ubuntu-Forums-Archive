---
title: "Ubuntu crashes and shuts down computer"
date: 2010-02-26
forum: General Help
---

### Post by atnmitch on 2010-02-26
Hello, 
I have been using Ubuntu for about a month now, it works well except for one problem which can be very distressing. 
What happens is that the computer just shuts down instantly with no prior warning. As it shuts down the light indicating the laptop is plugged in turns off, despite it still being plugged in and have to unplug and plug it back in about 20 seconds later. When I turn it back it works as if nothing has happened and works fine until next time it happens.
The only explanation is that firefox was open everytime it happened and either watching bbc iplayer live or using the Mibbit chat application, I assume these have something to do with this but cannot understand or solve this problem.
I am using ubuntu 9.10 and have booted on the 2.6.30.14 and 2.6.30.19 and happens on both.
Any help would be very welcome.
Thank you.

---

### Post by Mark Phelps on 2010-02-26
Laptops are very sensitive to heat, and there have been quite a few  posts dealing with overheating and Ubuntu 9.10.

If you want to diagnose the problem, presuming it IS overheating, then you need to install the lm-sensors package, configure it using "sudo sensors-detect", install the module lines, reboot the laptop, and monitor the CPU temperature(s).

---

