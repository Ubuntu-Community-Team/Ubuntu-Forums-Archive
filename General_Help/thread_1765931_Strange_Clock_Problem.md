---
title: "Strange Clock Problem"
date: 2011-05-23
forum: General Help
---

### Post by mataug on 2011-05-23
I've a Ubuntu 10.04 (64-bit) desktop and Ubuntu 8.04 (32-bit) installed in virtualbox on this machine.

I've had a strange problem for the last 3-4 days.

The clock on the desktop keeps slowing down, eventually going behind by 14-15 minutes over the course of 24 hours while the clock on the virtualbox ubuntu works perfectly fine :confused:

I have set the clock to the correct time thrice already but it is getting irritating to do this every morning I come to the lab :(

Any suggestions ?

---

### Post by coffee412 on 2011-05-23
> **mataug said:**
> I've a Ubuntu 10.04 (64-bit) desktop and Ubuntu 8.04 (32-bit) installed in virtualbox on this machine.

I've had a strange problem for the last 3-4 days.

The clock on the desktop keeps slowing down, eventually going behind by 14-15 minutes over the course of 24 hours while the clock on the virtualbox ubuntu works perfectly fine :confused:

I have set the clock to the correct time thrice already but it is getting irritating to do this every morning I come to the lab :(

Any suggestions ?

I have a suggestion. Check your logs (/var/log/messages) and see if your getting a "clocksource unstable" message. I had an interesting problem that involved that error but I really dont want to elaborate too much unless you are seeing it.

Anything else unusual showing up in the logs for your desktop version?

coffee

---

### Post by mataug on 2011-05-23
> **coffee412 said:**
> I have a suggestion. Check your logs (/var/log/messages) and see if your getting a "clocksource unstable" message. I had an interesting problem that involved that error but I really dont want to elaborate too much unless you are seeing it.

Anything else unusual showing up in the logs for your desktop version?

coffee

nope even the word clock doesn't exist in any of the log files

regarding stuff in the logs, there is a lot of lines like these:
> May 23 12:41:08 vision pulseaudio[1633]: ratelimit.c: 366 events suppressed
where vision is the name of my machine.... nothing else catches my attention

**However** before leaving in the evening, I changed the time settings to **Keep synchronized with Internet servers**
and now the time hasn't lagged behind in the 4 hours since then

but I would still like to know why a manual setting wasn't working :confused:

---

### Post by coffee412 on 2011-05-23
> **mataug said:**
> nope even the word clock doesn't exist in any of the log files

regarding stuff in the logs, there is a lot of lines like these:

where vision is the name of my machine.... nothing else catches my attention

**However** before leaving in the evening, I changed the time settings to **Keep synchronized with Internet servers**
and now the time hasn't lagged behind in the 4 hours since then

but I would still like to know why a manual setting wasn't working :confused:

Really dont know at this point. Its interesting that the older version works but not the 10.x version. But I did at one time have a problem where I was gettng errors like "Switching to TSC clock source" and other wierd clocksource errors. Sorry I cannot be of further help for you. Atleast the sync is working.

coffee

---

### Post by mataug on 2011-05-24
> **coffee412 said:**
> Really dont know at this point. Its interesting that the older version works but not the 10.x version. But I did at one time have a problem where I was gettng errors like "Switching to TSC clock source" and other wierd clocksource errors. Sorry I cannot be of further help for you. **Atleast the sync is working**.

coffee

Not any more... clock's gone 8 minutes behind in the last 24 hours :(

and now even the 32-bit guest ubuntu is showing the same wrong time as the host machine... this is really confusing :confused:

---

### Post by 5149.5 on 2011-05-24
Could this be due to the hardware clock being off substantially? I wouldn't expect the system clock to skew towards the hardware clock except at boot time though.

---

### Post by mataug on 2011-05-24
> **5149.5 said:**
> Could this be due to the hardware clock being off substantially? I wouldn't expect the system clock to skew towards the hardware clock except at boot time though.

I had the same doubt... will the system try to stay close to the hardware clock or not

---

### Post by 5149.5 on 2011-05-24
> **mataug said:**
> I had the same doubt... will the system try to stay close to the hardware clock or not

Get the system time back in sync with the ntp servers and then do:

```
hwclock -r
```

That will show you the current time according to the system clock. If you enter:
```
hwclock -w
```

it will set the hardware clock to the current system time.

---

### Post by mataug on 2011-05-24
> **5149.5 said:**
> Get the system time back in sync with the ntp servers and then do:

```
hwclock -r
```

That will show you the current time according to the system clock. If you enter:
```
hwclock -w
```

it will set the hardware clock to the current system time.

done what you have mentioned

when I read it using "hwclock -r", there was a 16 second difference between the output of that and "date"

I'm assuming the slight difference in seconds was because I had reset the time to its correct value after finding that it was lagging behind again today ?

---

