---
title: "Battery Reading Issue"
date: 2009-10-07
forum: General Help
---

### Post by doggbat on 2009-10-07
I have recently been having an odd problem with my battery in my HP Pavillion.  It has to do with the charging and discharging of the battery.

For some reason, the battery will not charge past 69.5%.  When it reaches 69.5%, it says it is fully charged, though when I hover over the battery icon, it tells me it is only 69.5% charged.  When I click the battery for device information it reads:

Product: Laptop battery
Status: Charged
Percentage charge: 69.5%
Vendor: Hewlett-Packard
Technology: Lithium Ion
Serial number: 
Model: Primary
Capacity: 75.2% (Fair)
Current charge: 28.9 Wh
Last full charge: 66.8 Wh
Design charge: 88.8 Wh
Charge rate: 0.0 

The other issue is that when discharging, the computer shuts down at around 25% battery charge, and will not boot again until it is plugged in.  I have tried fully charging the battery and then completely draining it many times with no results.  Any help is much appreciated.

Thanks,




doggbAT.

---

### Post by sedawk on 2009-10-07
There are two files you can look at:
```

cat /proc/acpi/battery/BAT0/state
cat /proc/apci/battery/BAT0/info

```

One field says "last full capacity" or similar
and one gives the total capacity.
Most likely your battery has aged and 
the value of "last full capacity" is around
70% of the total capacity.
There most likely is nothing you can do to
charge be battery beyond that point (anymore).

Normally your computer shouldn't shutdown when
capacity is still  25% but there might be other
factors involved.
Does the computer simply turn off or is the
"low battery" power shutdown initiated?
Normally the GUI also shows the remaining time - is
there anything suspicious about the remaining time?
E.g. is the remaining time far too low for 27% remaining
capacity (like 3 minutes)?

I once messed around with laptop that had a remaining
capacity of 30 minutes. All readings from its battery
were more or less useless ...

BTW: Lithium battery should suffer from memory effects, so
running full charge-decharge cycles shouldn't have any
impact on the capacity.

---

### Post by doggbat on 2009-10-07
Here are the results to the cat codes:
```
connor@Bee:~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6000 mAh
last full capacity:      4512 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 232 mAh
design capacity low:     140 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

connor@Bee:~$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      2400 mAh
present voltage:         14409 mV

```

The computer is currently unplugged and discharging. Since my update to the 9.10 beta, no battery life has been provided, though it does say "Laptop battery discharging (52.5%)".

The battery information does tell me that my battery is at 75% of its original capacity.. But before purchasing this battery, my old one had a capacity of 50%, and still charged to 100% on the battery bar(just to let you know that it is full).  That is fine though, and I can deal with it only charging to 69%.

The real issue is that the computer, around 25% just dies.  I'm not even sure what percentage it is at, because I will be listening to music or on facebook or something, and it will just die.  No shutdown sequence or anything, just a black screen and no power.  As I said, since my update to 9.10, no remaining time has been available to me, but when I was running 9.04 a couple days ago, the discharge time seemed normal -- it would just shut down when there were about forty minutes left.

Thanks for the help




doggbAT.

---

### Post by doggbat on 2009-10-09
bump..?

---

