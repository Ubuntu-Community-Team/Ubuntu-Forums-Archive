---
title: "Stress testing GPU/CPU, and temperatures"
date: 2010-10-05
forum: General Help
---

### Post by Aizawa on 2010-10-05
Ahoy!

After turning off the overclocking (When I actually turned it off, I realized it didn't really make a noticeable difference) of my CPU and lowering the fans of my PC, I would like to stress test the GPU/CPU, and obviously also check the temps while doing so.

The fans on my PC were previously so loud you couldn't even have a conversation on the phone while in the same room as the computer, and I just now realized how much I can actually lower them... But I don't want to lower them too much, obviously.

So, anyway, because of these reasons I would like to stress test my CPU/GPU while monitoring the temperatures.
I'd need software for doing so, Linux or Windows doesn't really matter, I have both.
Also, I need to know what minimum/maximum temperatures that are okay.

Thank you in advance, and I hope it's okay to ask this in this forum/subforum! (EDIT: Should probably have put it in the Hardware forum, but I don't know how to move/remove this thread! :()

---

### Post by ridgeland on 2010-10-06
From my notes when I installed Ubuntu 10.04:

> $ sensors  --- then follow the prompts to install sensors-detect
$ sudo sensors-detect 
    scan ISA/IO ports default NO - I said yes (still none found)
    add lines to /etc/modules default NO - I said yes

Reboot

$ sensors  --- should now show all fans and some temps.
synaptics - install sensors-applet --- option hddtemp deamon on boot - Yes

modify panel 
- add - hardware sensors, 

On the panel I have CPU fan and case fan and temperatures of the CPU and hard drives.
My old Dell PC cannot display fan speeds.
Manufacturers say what temperature range to use.

---

