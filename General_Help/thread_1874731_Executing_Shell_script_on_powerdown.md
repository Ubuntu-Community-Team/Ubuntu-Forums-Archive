---
title: "Executing Shell script on powerdown"
date: 2011-11-03
forum: General Help
---

### Post by Yashwanth_kp on 2011-11-03
Hi,

I wanted to know how i could execute a shell script when power supply is cutoff from my laptop.

I tried placing the file in /usr/lib/pm-utils/power.d/ which is called when power  is cutoff from laptop..

But there script is not initiated at all...

I used the /usr/lib/pm-utils/power.d/ and placed files which automatically disable bluetooth when power was cutoff..

But i am unable to execute a shell script doing the same thing...

plz help

---

### Post by SteveDee on 2011-11-04
> **Yashwanth_kp said:**
> ...I wanted to know how i could execute a shell script when power supply is cutoff from my laptop....

Could you monitor the AC state and perform tasks when AC goes off-line?

For example, using this command:-
```

cat /proc/acpi/ac_adapter/AC/state

```
...will return:-
```

state:                   on-line

```
...if AC power is available, or:-
```

state:                   off-line

```
...when AC power is removed.

---

