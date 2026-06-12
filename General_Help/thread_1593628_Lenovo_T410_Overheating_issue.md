---
title: "Lenovo T410 Overheating issue"
date: 2010-10-11
forum: General Help
---

### Post by sridatta on 2010-10-11
I just installed Ubuntu 10.10 on my Lenovo Thinkpad T410. Everyone works smoothly but the system quickly heats up even when idle. I get the following error in my /var/log/syslog:

Oct 11 12:22:05 sridatta-ThinkPad-T410 kernel: [ 1331.612799] Critical temperature reached (128 C), shutting down.
Oct 11 12:22:05 sridatta-ThinkPad-T410 kernel: [ 1331.620215] Critical temperature reached (128 C), shutting down.

Any advice?

---

### Post by steve_d on 2010-10-16
Check out thinkwiki

[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

I had a problem on my mac with overheating, the min fan speed was set too low and I had to boost it up to avoid overheating.

Steve

---

### Post by TBABill on 2010-10-16
128C is a crazy high temp to hit. I hit 86 on a laptop once and I was literally sweating trying to use it. I was not blocking the vents at all and it just kept climbing so I shut it down at 86. How you got to 128 is very important. Can you run the command "top" from a terminal and see what is eating all your CPU? And probably it is something also eating your GPU.

Are you using the proprietary video driver for your machine? That's not the fix to this problem, just wondering if you are using open source or proprietary video.

You may also want to install htop and then run the command "htop" from a terminal and check its output as well.

---

### Post by GooglieS on 2010-12-17
I have the same problem. I have t410 laptop with nvidia 3100. And this thing happend with me after I install NVIDIA proprietary driver. Don't know how to fix this.

---

### Post by Blue-Tiger on 2011-03-21
Hi!
I thought I'd bring this up again. Since I upgraded to 11.04 alpha, I'm experiencing the same problems. Every time this happens, I am watching some video. I don't think the temperature really reaches critical levels though (right now I'm watching a video, and 'acpi -t' shows ~66 deg.), so this looks like some sort of driver issue.

---

