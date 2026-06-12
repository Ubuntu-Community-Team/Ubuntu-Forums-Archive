---
title: "Going Green - PowerTop and cutting on power consumption"
date: 2010-02-27
forum: General Help
---

### Post by Lockheed on 2010-02-27
Judging by the number of responses (close to zero) to other threads about powertop on this forum, I have little hope in getting any answers. However, I do not know where else could I ask.

PowerTop tell me that even after applying almost all the tips and tricks from lesswatts.org, my laptop still consumes over 72 Watts while idling.
```
< Detailed C-state information is not P-states (frequencies)
                                        1.60 Ghz     0.0%
                                         800 Mhz   100.0%




Wakeups-from-idle per second : 451.1    interval: 10.0s
Power usage (5 minute ACPI estimate) :  72.5 W (0.3 hours left)

Top causes for wakeups:
  45.3% (407.4)      <kernel IPI> : Rescheduling interrupts 
  29.9% (269.2)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   7.2% ( 65.1)       <interrupt> : extra timer interrupt 
   5.6% ( 50.0)       touchfreeze : hrtimer_start_range_ns (hrtimer_wakeup) 
   5.3% ( 48.1)       <interrupt> : ath 
   1.9% ( 17.4)   thunderbird-bin : hrtimer_start_range_ns (hrtimer_wakeup) 
   1.0% (  9.1)       <interrupt> : nvidia
   0.6% (  5.8)        cairo-dock : hrtimer_start_range_ns (hrtimer_wakeup)
   0.6% (  5.0)     <kernel core> : hrtimer_start (tick_sched_timer)
   0.3% (  3.0)       rainlendar2 : hrtimer_start_range_ns (hrtimer_wakeup)
   0.3% (  2.6)      <kernel IPI> : TLB shootdowns
   0.2% (  2.0)       <interrupt> : sata_nv
   0.2% (  2.0)   thunderbird-bin : sk_reset_timer (tcp_write_timer)
   0.2% (  2.0)           emerald : hrtimer_start_range_ns (hrtimer_wakeup)
   0.2% (  1.7)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  1.3)     <kernel core> : sk_reset_timer (tcp_delack_timer)
   0.1% (  1.1)        checkgmail : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  1.0)         cpupowerd : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  1.0)     <kernel core> : nv_kern_rc_timer (nv_kern_rc_timer)
   0.1% (  0.7)        gam_server : hrtimer_start_range_ns (hrtimer_wakeup)

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

```
This is when I am not touching the laptop. When I am surfing the web or listen to music, it goes up to 2000+ wakeups!

How do I cut it further? I am getting like 20-30 minutes max on battery and this is unacceptable cause in Windows I get at least 3 times that.

---

### Post by hwttdz on 2010-02-28
uname -a?

Also do you have a kill-a-watt or similar?  I wonder if it's really using 70+ watts, but in any case 30 minutes is unacceptable and shouldn't happen.  I wonder if we can do something to get c-state information, because if the processor isn't dropping down to the proper c-state we could be using a bunch of unnecessary power.  

So you have laptop mode enabled?  and dirty writeback set to 1500?  

Here might be a few other things to try: 
[http://www.smop.co.uk/mediawiki/index.php/Power_saving_on_Linux](http://www.smop.co.uk/mediawiki/index.php/Power_saving_on_Linux)

I would probably go for building your own powertop to get an updated version and the most information.  And I think there's something funny going on such that it's rescheduling so much.

---

### Post by Lockheed on 2010-02-28
> **hwttdz said:**
> uname -a?
2.6.32.9-newyork #1 SMP Sat Feb 27 22:34:59 GMT 2010 x86_64 GNU/Linux

> **hwttdz said:**
> Also do you have a kill-a-watt or similar?  I wonder if it's really using 70+ watts, but in any case 30 minutes is unacceptable and shouldn't happen.  I wonder if we can do something to get c-state information, because if the processor isn't dropping down to the proper c-state we could be using a bunch of unnecessary power.  
No kill-a-watt. I have some voltage/ampero-meter but that probably would not tell me much.
Not sure what you mean by c-state information. I am not using built-in governor, but a third-party cpupowerd which enables me not only to downclock the cpu, but also undervolt it. It is working fine.

> **hwttdz said:**
> So you have laptop mode enabled?  and dirty writeback set to 1500?  
laptop mode is on. I do not know what is dirty feedback but if it is set by **/sys/vm/dirty_writeback_centisecs**, then I do not have VM  folder, let alone the file.

> **hwttdz said:**
> Here might be a few other things to try: 
[http://www.smop.co.uk/mediawiki/index.php/Power_saving_on_Linux](http://www.smop.co.uk/mediawiki/index.php/Power_saving_on_Linux)
I already have most of those enabled but will apply the rest.

When I set 2D GPU to 50% of it's nominal value, nvidia-settings resets it back to 100 when I cluck Apply.

---

### Post by hwttdz on 2010-02-28
There's a bug in the nvidia thing that makes you use the sliders instead of the text boxes.

C states are the various sleep states that your processor can enter into (not to be confused with sleeping the whole machine), it can cut power to one cpu core at a time, reducing power consumption.  

It looks like for some reason you have many processes which are being juggled between cores, which is preventing any of the cores from sleeping (i.e. so many rescheduling interrupts).

---

### Post by hwttdz on 2010-02-28
Also a little googling tells me on some machines it's due to hyperthreading screwing up.  Of course you theoretically give up some performance by disabling it (and you might not even have a machine with hyperthreading).

Looks like it might also be a ubuntuone problem.  Many report improvement after removing/disabling it.  I think there are a few other options for backups, rsync probably being the most robust. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/373245](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/373245)

---

