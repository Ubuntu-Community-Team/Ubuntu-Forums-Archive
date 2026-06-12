---
title: "Wrong Time"
date: 2012-07-26
forum: General Help
---

### Post by Hungry Man on 2012-07-26
I don't know what the issue is but I keep setting my clock to New York and it keeps telling me the wrong time.

It's nearly 2 and it's telling me it's 9:30am.

I've tried switching to one time zone and switching back. The manual time doesn't seem to even work...

---

### Post by plucky on 2012-07-26
> **Hungry Man said:**
> I don't know what the issue is but I keep setting my clock to New York and it keeps telling me the wrong time.

It's nearly 2 and it's telling me it's 9:30am.

I've tried switching to one time zone and switching back. The manual time doesn't seem to even work...

Desktop or Laptop?

Could be the battery is dead.

Good Luck

---

### Post by Hungry Man on 2012-07-26
Laptop. The battery is working fine and Windows' time is fine.

---

### Post by papibe on 2012-07-26
Hi Hungry Man.

Could you post the results of these commands?
```
cat /etc/timezone

grep -i utc /etc/default/rcS

sudo hwclock --show

date +%z
```
Regards.

---

### Post by efflandt on 2012-07-26
Windows typically sets the CMOS clock/calendar to localtime, and the default for Linux is to set CMOS clock/calendar to UTC.  During install Linux would usually figure out whether that is localtime or UTC.  Maybe in your case it did not, but the difference between EDT (-0400) and UTC should be 4 hours.

---

### Post by Hungry Man on 2012-07-26
> root@colin-ubuntu:/home/colin# grep -i utc /etc/default/rcS
# assume that the BIOS clock is set to UTC time (recommended)
UTC=yes
root@colin-ubuntu:/home/colin# 
root@colin-ubuntu:/home/colin# sudo hwclock --show
Thu 26 Jul 2012 06:02:09 PM EDT  -0.830056 seconds
root@colin-ubuntu:/home/colin# 
root@colin-ubuntu:/home/colin# date +%z
-0400
root@colin-ubuntu:/home/colin# 

I think either Windows is hours off or Linux is hours off.

---

### Post by papibe on 2012-07-26
Thanks.

You missed 'cat /etc/timezone', but I'll assume it says 'America/NY' or similar.

If the time you see with hwclock is your local time, then modify to 'no', the grep'ed line on the file /etc/default/rcS

Restart, and let us know how it goes.
Regards.

---

### Post by Hungry Man on 2012-07-26
That's not the right time.

---

### Post by asmoore82 on 2012-07-27
If you're going to dual boot with windows, you'll have to set linux to use localtime, then restart, then set the clock one more time.

```
gksudo gedit /etc/default/rcS
```

and change the line to "UTC=no"

---

### Post by Hungry Man on 2012-07-27
Thanks. Hopefully it sticks and doesn't mess with my Windows time.

---

