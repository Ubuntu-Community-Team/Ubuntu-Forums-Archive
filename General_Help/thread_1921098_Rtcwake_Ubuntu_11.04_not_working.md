---
title: "Rtcwake Ubuntu 11.04 not working"
date: 2012-02-06
forum: General Help
---

### Post by jorovifi on 2012-02-06
Hi everyone, I'm trying to wake up my PC through rtcwake command. 

I've try this and all the variants, 

> sudo rtcwake -u -s 40 -m memI've read issues, forums, tutos and manuals. I think rtcwake works 'cause in mode 'on' & 'no' the process finishes, showing this

> rtcwake: wakeup from "mem" using /dev/rtc0 at Mon Feb  6 09:21:14 2012 and similar

And the PC suspends nice, but the problem is that never goes back, I mean, never wakes up! In the BIOS there's a function to make an event manually and it works! 

I really need help! I wanna turn my PC into Alarm! 

- Ubuntu 11.04 x86
- Linux Kernel 2.6.38-13 generic
- Foxconn A7GM-s 2.0

---

### Post by Rodney9 on 2012-02-06
Two sites I found useful - 

[http://crunchbanglinux.org/forums/topic/11054/alarm-clock/](http://crunchbanglinux.org/forums/topic/11054/alarm-clock/)

[http://xrubenx.blogspot.com.au/2011/03/wake-up-alarm-on-linux.html](http://xrubenx.blogspot.com.au/2011/03/wake-up-alarm-on-linux.html)

I use -

```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```

in combination with Alarm Clock

Rodney

---

### Post by jorovifi on 2012-02-06
Thanks for answering so fast!! the -t option is the another way to set the time, -s is for "seconds".

I've seen in support for my MB that some update fixes something written as "sleep s3 bug fix" so I don't know if there's on the BIOS, but I've never flashed it before

thanks!

---

