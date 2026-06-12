---
title: "cpu scaling (set default)"
date: 2010-05-02
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-05-02
i found this
[http://ubuntuforums.org/showthread.php?t=574803](http://ubuntuforums.org/showthread.php?t=574803)
but the setting is not there in 10.04 and idea where it is?

---

### Post by dcstar on 2010-05-03
> **pqwoerituytrueiwoq said:**
> i found this
[http://ubuntuforums.org/showthread.php?t=574803](http://ubuntuforums.org/showthread.php?t=574803)
but the setting is not there in 10.04 and idea where it is?

Modify /etc/init.d/ondemand to whatever you want or install the **powernowd** package.

---

### Post by pqwoerituytrueiwoq on 2010-05-03
thanks
edited line 27 of ondemand
new line 27
```
        echo -n conservative > $CPUFREQ # conservative was ondemand
```
powernowd does not appear to have a governor settings

---

### Post by drew314 on 2010-07-09
My line 27 setting was 
```
               echo -n ondemand > $CPUFREQ
```
But my default scaling was performance according to the CPU Frequency Scaling Monitor.
I installed powernowd and it looks to be following the /etc/init.d/ondemand now. 

Thanks for the info.

---

