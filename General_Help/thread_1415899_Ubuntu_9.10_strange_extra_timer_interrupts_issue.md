---
title: "Ubuntu 9.10 strange extra timer interrupts issue"
date: 2010-02-25
forum: General Help
---

### Post by Jorn Skorstad on 2010-02-25
Hi, I have observed some strange behaviour of interrupts. See the following output from powertop:

Uptime 5 minutes
Wakeups-from-idle per second : 86,8	interval: 15,0s
no ACPI power usage estimate available
Top causes for wakeups:
  37,8% (129,7)       <interrupt> : uhci_hcd:usb2, uhci_hcd:usb5, rr26xx 
  23,6% ( 81,0)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
  15,4% ( 52,9)       <interrupt> : eth0 
  12,9% ( 44,3)          icecast2 : hrtimer_start_range_ns (hrtimer_wakeup) 

Uptime 3 days
Wakeups-from-idle per second : 110,9	interval: 15,0s
no ACPI power usage estimate available
Top causes for wakeups:
  38,7% (170,1)       <interrupt> : extra timer interrupt 
  18,1% ( 79,4)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
  12,3% ( 54,1)       <interrupt> : eth0 

Uptime 11 days
Wakeups-from-idle per second : 251,5	interval: 15,0s
no ACPI power usage estimate available
Top causes for wakeups:
  81,3% (814,3)       <interrupt> : extra timer interrupt 
   7,6% ( 75,9)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   5,0% ( 50,0)          icecast2 : hrtimer_start_range_ns (hrtimer_wakeup) 
   1,2% ( 12,4)       <interrupt> : eth0 

As you can see, when system is "fresh" booted there are no noticeable "Extra timer interrupts". As time goes, this number seems to increase. I have tried to find out what causes this behaviour without any luck. I am not even sure if this is any practical problem, as performance seems to be more or less unaffected, but any explanation to this would be nice. Anyone else ever notice this?

I am running Ubuntu 9.10 Server edition on a Dell Poweredge SC1420, 64-bit version. The server is used for web and file sharing mostly, with little load. (15 min avg. about 0,10).

To be mentioned, I never noticed this behaviour in previous Ubuntu versions (used 7.10 and 8.04 earlier).

---

### Post by Jorn Skorstad on 2010-03-05
<bump>

Noone?
Here is numbers from today, 19 days uptime:
Wakeups-from-idle per second : 475,4	interval: 15,0s
no ACPI power usage estimate available
Top causes for wakeups:
  74,4% (1412,1)       <interrupt> : extra timer interrupt 
   7,6% (143,4)       <interrupt> : eth0 
   5,2% ( 97,9)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   4,0% ( 76,7)            python : hrtimer_start_range_ns (hrtimer_wakeup) 
   2,6% ( 49,9)          icecast2 : hrtimer_start_range_ns (hrtimer_wakeup) 

It seems Extra timer interrupts are increasing a little every day. I have noticed similar behaviour on my laptop as well (also running Ubuntu 9.10, i386 version)

---

### Post by yankee83 on 2011-09-29
Hi Jorn,

Did you manage to fix this problem?

---

### Post by Jorn Skorstad on 2011-09-29
Hi Yankee83,

yes in a way I have solved it. I installed Debian 5 Lenny, and this issue was gone. I never found a solution with Ubuntu. 

Current kernel in Lenny is 2.6.26-2, maybe the answer lies here...

---

### Post by yankee83 on 2011-10-05
Hi Jorn,

Thanks for your answer. I tried to run the 2.6.26 kernel version on Natty without success. Since I don't feel like tampering with my system, I'll just leave it as it is for now and wait for a fix :)

---

