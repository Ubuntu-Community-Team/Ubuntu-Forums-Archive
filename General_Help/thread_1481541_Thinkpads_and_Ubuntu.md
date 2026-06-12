---
title: "Thinkpads and Ubuntu"
date: 2010-05-12
forum: General Help
---

### Post by danbuter on 2010-05-12
I may be getting a Thinkpad soon. I just had a couple questions about them and compatibility with 10.4.

1. Does the track button work correctly?
2. Are there any weird graphics or speaker issues?
3. Will the laptop correctly go to sleep and wake up when I close and open the lid?

Thanks!

---

### Post by marbss on 2010-05-13
> **danbuter said:**
> I may be getting a Thinkpad soon. I just had a couple questions about them and compatibility with 10.4.

1. Does the track button work correctly?
2. Are there any weird graphics or speaker issues?
3. Will the laptop correctly go to sleep and wake up when I close and open the lid?

Thanks!


what thinkpad are you getting?  there are many types of thinkpads....

---

### Post by conmat on 2010-05-13
I'm running 9.10 64-bit on a T400.  I have the following problems:

1.  Random crashes.  No one has been able to provide a fix.
2. Short battery life.  A six-cell battery gives ~3hrs with integrated Intel graphics.  ~2hrs with ATI graphics!
3.  I bought a T400 with switchable graphics.  You CAN NOT switch graphics in Ubuntu.   I refuse to accept that rebooting my system and changing BIOS setting qualifies as switchable graphics!
4.  If you buy a new Thinkpad and install another OS Lenovo will probably void your warranty.


Everything else works O.K.  I will upgrade to 10.4 soon.  I hope this will fix my problems.

Trackpad and trackpoint work fine.
Suspend works fine.  I just close the screen and my system suspends automatically.
Proprietary ATI drivers will destroy your installation.
There are some quirks with graphics players.  I forget but you may have to do a google search for some fixes.

If you want an absolutely stable system you should probably look at system76 or a similar Linux company.

---

### Post by Seq on 2010-05-13
What model are you getting? I've got a T510 on order. Apparently adding a webcam put me on backorder. :/

> **conmat said:**
> I'm running 9.10 64-bit on a T400.  I have the following problems:

1.  Random crashes.  No one has been able to provide a fix.

This is running the intel X4500 graphics on a Core 2 Duo? I haven't heard of any thinkpad-specific stability issues. I'd be interested to read the bug though (not that I can help, really. Just curiosity).

> **conmat said:**
> 2. Short battery life.  A six-cell battery gives ~3hrs.

What does powertop put your power utilization at? Also, what is the difference if you toggle between the graphics drivers?

> **conmat said:**
> 3.  I bought a T400 with switchable graphics.  You CAN NOT switch graphics in Ubuntu.   I refuse to accept that rebooting my system and changing BIOS setting qualifies as switchable graphics!

One of the biggest limitations currently is Xorg. The proprietary drivers (your discrete card) still want a static config, while the open drivers (your intel card) are fine with probing. Not only would you need to have hardware hand-over, Xorg would at the very least need a restart and config swap.

Somewhat unfortunate that these things don't work more seamlessly at the moment. There has been some preliminary work I've seen on planet freedesktop regarding switchable graphics, but it is still rough around the edges.

> **conmat said:**
> 4.  If you buy a new Thinkpad and install another OS Lenovo will probably void your warranty.

I've never heard of this, and I'd be quite surprised if that was the case. They issued a bios update for the T510 specifically to fix ACPI suspend issues with "non-windows" operating systems.

> **conmat said:**
> If you want an absolutely stable system you should probably look at system76 or a similar Linux company.

I can't argue that. If you want a laptop that absolutely *does* work with Linux, buy from somebody that has tested it.

---

### Post by conmat on 2010-05-14
My replies are inline:


This is running the intel X4500 graphics on a Core 2 Duo? I haven't heard of any thinkpad-specific stability issues. I'd be interested to read the bug though (not that I can help, really. Just curiosity).


***
Here is the syslog from my latest crash:
May 14 20:15:47 foobar dhclient: bound to 134.60.236.42 -- renewal in 89 seconds.
May 14 20:17:01 foobar CRON[14065]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 14 20:17:16 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:17:16 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:17:16 foobar dhclient: bound to 134.60.236.42 -- renewal in 83 seconds.
May 14 20:18:39 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:18:39 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:18:39 foobar dhclient: bound to 134.60.236.42 -- renewal in 71 seconds.
May 14 20:19:50 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:19:50 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:19:50 foobar dhclient: bound to 134.60.236.42 -- renewal in 82 seconds.
May 14 20:21:12 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:21:12 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:21:12 foobar dhclient: bound to 134.60.236.42 -- renewal in 74 seconds.
May 14 20:22:26 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:22:26 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:22:26 foobar dhclient: bound to 134.60.236.42 -- renewal in 87 seconds.
May 14 20:23:53 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:23:53 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:23:53 foobar dhclient: bound to 134.60.236.42 -- renewal in 78 seconds.
May 14 20:25:11 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:25:11 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:25:11 foobar dhclient: bound to 134.60.236.42 -- renewal in 74 seconds.
May 14 20:26:25 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:26:25 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:26:25 foobar dhclient: bound to 134.60.236.42 -- renewal in 75 seconds.
May 14 20:27:40 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:27:40 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:27:40 foobar dhclient: bound to 134.60.236.42 -- renewal in 92 seconds.
May 14 20:29:12 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:29:12 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:29:12 foobar dhclient: bound to 134.60.236.42 -- renewal in 90 seconds.
May 14 20:30:42 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:30:42 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:30:42 foobar dhclient: bound to 134.60.236.42 -- renewal in 71 seconds.
May 14 20:31:53 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:31:53 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:31:53 foobar dhclient: bound to 134.60.236.42 -- renewal in 87 seconds.
May 14 20:33:20 foobar dhclient: DHCPREQUEST of 134.60.236.42 on wlan0 to 134.60.1.23 port 67
May 14 20:33:20 foobar dhclient: DHCPACK of 134.60.236.42 from 134.60.1.23
May 14 20:33:20 foobar dhclient: bound to 134.60.236.42 -- renewal in 85 seconds.

VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV

Crash is here

Below is reboot

^^^^^^^^^^^^^^^^^^^^^^^^^^^

May 14 20:34:57 foobar kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
May 14 20:34:57 foobar rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1443" x-info="http://www.rsyslog.com"] (re)start
May 14 20:34:57 foobar rsyslogd: rsyslogd's groupid changed to 103
May 14 20:34:57 foobar rsyslogd: rsyslogd's userid changed to 101
May 14 20:34:57 foobar rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
May 14 20:34:57 foobar kernel: [    0.000000] Initializing cgroup subsys cpuset
May 14 20:34:57 foobar kernel: [    0.000000] Initializing cgroup subsys cpu
May 14 20:34:57 foobar kernel: [    0.000000] Linux version 2.6.32-020632-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #020632 SMP Thu Dec 3 10:09:58 UTC 2009
May 14 20:34:57 foobar kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-020632-generic root=/dev/mapper/sfs-root ro quiet splash
May 14 20:34:57 foobar kernel: [    0.000000] KERNEL supported cpus:
May 14 20:34:57 foobar kernel: [    0.000000]   Intel GenuineIntel
May 14 20:34:57 foobar kernel: [    0.000000]   AMD AuthenticAMD
May 14 20:34:57 foobar kernel: [    0.000000]   Centaur CentaurHauls



What does powertop put your power utilization at? Also, what is the difference if you toggle between the graphics drivers?

***
I don't use the ATI card at all anymore.  I don't trust the drivers and battery life is only two hours.  Here is powertop output:

    PowerTOP version 1.11      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.2%)         2.54 Ghz     0.7%
polling           0.0ms ( 0.0%)         2.54 Ghz     0.0%
C1 mwait          0.0ms ( 0.0%)         1.60 Ghz     0.3%
C2 mwait          0.2ms ( 0.1%)          800 Mhz    99.0%
C4 mwait          3.5ms (95.7%)

Wakeups-from-idle per second : 274.7    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  36.6% (126.2)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  15.2% ( 52.4)       <interrupt> : extra timer interrupt 
  13.2% ( 45.6)       <interrupt> : iwlagn 
   8.8% ( 30.2)      <kernel IPI> : Rescheduling interrupts 
   7.7% ( 26.4)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   3.8% ( 13.2)       <interrupt> : ahci 

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequently for background VM activity
 Q - Quit   R - Refresh   W - Increase Writeback time 



One of the biggest limitations currently is Xorg. The proprietary drivers (your discrete card) still want a static config, while the open drivers (your intel card) are fine with probing. Not only would you need to have hardware hand-over, Xorg would at the very least need a restart and config swap.

Somewhat unfortunate that these things don't work more seamlessly at the moment. There has been some preliminary work I've seen on planet freedesktop regarding switchable graphics, but it is still rough around the edges.


***
I'm not really unhappy that I can't switch graphics on the fly.  It would be nice but it's not that big a deal for me.  I just wish the ATI card didn't drain the battery so fast



I've never heard of this, and I'd be quite surprised if that was the case. They issued a bios update for the T510 specifically to fix ACPI suspend issues with "non-windows" operating systems.

***
I hope you are right.
Here is a link to Lenovo's warranty:
[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/l505-0010-01-en.pdf](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/l505-0010-01-en.pdf)

Here are some quotes from the warranty.  These are weasel words that Lenovo can use to deny warranty coverage if you install Linux:

Before your Service Provider replaces a product or part, you agree to:
1. remove all features, parts, options, alterations, and attachments not under warranty service;

What this Warranty Does not Cover
This warranty does not cover the following:
-----------------------------------
failure or damage resulting from misuse, accident, modification, unsuitable physical or operating environment, natural disasters,
power surges, or improper maintenance by you;
----------------------------------

The best solution I have read is just remove the harddrive before you send in your notebook for warranty service.  Say the drive has medical data and is covered by HIPPA.

---

### Post by Seq on 2010-05-14
> **conmat said:**
> My replies are inline:


This is running the intel X4500 graphics on a Core 2 Duo? I haven't heard of any thinkpad-specific stability issues. I'd be interested to read the bug though (not that I can help, really. Just curiosity).


***

(snip debug output)

Have you submitted the bug in Launchpad?

> **conmat said:**
> What does powertop put your power utilization at? Also, what is the difference if you toggle between the graphics drivers?

***
I don't use the ATI card at all anymore.  I don't trust the drivers and battery life is only two hours.  Here is powertop output:

```
    PowerTOP version 1.11      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.2%)         2.54 Ghz     0.7%
polling           0.0ms ( 0.0%)         2.54 Ghz     0.0%
C1 mwait          0.0ms ( 0.0%)         1.60 Ghz     0.3%
C2 mwait          0.2ms ( 0.1%)          800 Mhz    99.0%
C4 mwait          3.5ms (95.7%)

Wakeups-from-idle per second : 274.7    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  36.6% (126.2)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  15.2% ( 52.4)       <interrupt> : extra timer interrupt 
  13.2% ( 45.6)       <interrupt> : iwlagn 
   8.8% ( 30.2)      <kernel IPI> : Rescheduling interrupts 
   7.7% ( 26.4)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   3.8% ( 13.2)       <interrupt> : ahci 

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequently for background VM activity
 Q - Quit   R - Refresh   W - Increase Writeback time 
```


You ran this while plugged in? ("no ACPI power usage estimate available"). If you run it while on battery it will show how much power you're using. My current laptop (a macbook) is at 17 W with the screen brightness turned down, an goes to 27 with the brightness up. Essentially 1/3 of the power useage at full brightness is the screen. Handy way to extend battery if your room's lighting conditions permit.

> **conmat said:**
> One of the biggest limitations currently is Xorg. The proprietary drivers (your discrete card) still want a static config, while the open drivers (your intel card) are fine with probing. Not only would you need to have hardware hand-over, Xorg would at the very least need a restart and config swap.

Somewhat unfortunate that these things don't work more seamlessly at the moment. There has been some preliminary work I've seen on planet freedesktop regarding switchable graphics, but it is still rough around the edges.


***
I'm not really unhappy that I can't switch graphics on the fly.  It would be nice but it's not that big a deal for me.  I just wish the ATI card didn't drain the battery so fast

My model has non-switchable nvidia "workstation" graphics. My current machine has an nvidia 9600M GT, and while their drivers' performance is good, the feature support is not. no xrandr, no per-output colour profiles, etc.

Hopefully power consumption will be better than my current machine. I somewhat wish I was back to running intel graphics model like I used to (everything just worked), but that might not be the case right now.. :(

> **conmat said:**
> I've never heard of this, and I'd be quite surprised if that was the case. They issued a bios update for the T510 specifically to fix ACPI suspend issues with "non-windows" operating systems.

***
I hope you are right.
Here is a link to Lenovo's warranty:
[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/l505-0010-01-en.pdf](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/l505-0010-01-en.pdf)

Here are some quotes from the warranty.  These are weasel words that Lenovo can use to deny warranty coverage if you install Linux:

Before your Service Provider replaces a product or part, you agree to:
1. remove all features, parts, options, alterations, and attachments not under warranty service;

What this Warranty Does not Cover
This warranty does not cover the following:
-----------------------------------
failure or damage resulting from misuse, accident, modification, unsuitable physical or operating environment, natural disasters,
power surges, or improper maintenance by you;
----------------------------------

The best solution I have read is just remove the harddrive before you send in your notebook for warranty service.  Say the drive has medical data and is covered by HIPPA.

I don't think you'd need to say HIPPA. Unless the hard drive was the part you're replacing, I believe you can just say you're hanging on to it. They'll be running hardware test suites anyway.

---

### Post by danbuter on 2010-05-14
Not sure which Thinkpad I'll be getting. Possibly an R series. I just would like a good laptop, and I've heard almost 99% good things about Thinkpads. I was worried that they might have issues with Ubuntu, but I guess Lenovo is well-supported.:)

---

### Post by conmat on 2010-05-16
> You ran this while plugged in? ("no ACPI power usage estimate available"). If you run it while on battery it will show how much power you're using. My current laptop (a macbook) is at 17 W with the screen brightness turned down, an goes to 27 with the brightness up. Essentially 1/3 of the power useage at full brightness is the screen. Handy way to extend battery if your room's lighting conditions permit.Crap!  Yes, I ran this while plugged in.  I didn't realize I had to be running on battery only, but it makes sense.

Here is on battery only (even after enabling all the suggestions.  Still only three hours on battery):

```

     PowerTOP version 1.11      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 6.7%)         2.54 Ghz    10.8%
C0                0.0ms ( 0.0%)         2.54 Ghz     0.0%
C1 mwait          0.0ms ( 0.0%)         1.60 Ghz     1.3%
C2 mwait          0.3ms ( 0.1%)          800 Mhz    87.9%
C4 mwait          1.7ms (93.1%)

Wakeups-from-idle per second : 540.8    interval: 3.0s
Power usage (ACPI estimate): 14.9W (3.0 hours)

Top causes for wakeups:
  45.9% (296.7)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  22.5% (145.3)       <interrupt> : iwlagn 
  10.3% ( 66.3)       <interrupt> : extra timer interrupt 
   6.4% ( 41.7)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   3.4% ( 22.0)      <kernel IPI> : Rescheduling interrupts 
   1.5% ( 10.0)   ubuntuone-syncd : hrtimer_start_range_ns (hrtimer_wakeup) 
```Screen is full brightness but my screen looks like crap at anything else.  It is LED backlight.

Thanks for your suggestions.

---

