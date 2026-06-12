---
title: "Control fan speed using the radeon drivers?"
date: 2011-05-02
forum: General Help
---

### Post by olof_ on 2011-05-02
I am having slightly stability issues using the radeon driver as my gpu is idling around 60 degrees celsius. I have read about power modes and such, but I am looking for a way to just control the fan speed. Using fglrx, there was the following command:```
aticonfig --pplib-cmd 'set fanspeed 0 50'
```
is there any similar when using the radeon driver?

---

### Post by olof_ on 2011-05-08
no one?

---

### Post by clhsharky on 2011-05-08
olof_


To control your AMD Radeon gaming card you will need FGLRX driver.

OSS radeon driver will set defaults for your particular card bios.
> I have read about power modes and such
Power modes are for mobile chips and does not work on your card.
> using the radeon driver as my gpu is idling around 60 degrees celsius.
That seams normal for ATI with radeon OSS, mine runs 61c.
GPU chips can go 90+c safely.

More info on Open-Source AMD/ATI Linux
[http://phoronix.com/forums/forumdisplay.php?43-Open-Source-AMD-ATI-Linux](http://phoronix.com/forums/forumdisplay.php?43-Open-Source-AMD-ATI-Linux)


Sharky

---

### Post by olof_ on 2011-05-10
Thank you so much for the information.

I do use the radeon driver because I had some rather rough issues with fglrx and flash, and decided to give the free drivers a try. So far I do not regret it, but I have not tried any games yet, I will see about it more then. But that was not the discussion here. I will have a look at the link. Again, thank you.

---

