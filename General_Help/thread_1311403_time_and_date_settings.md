---
title: "time and date settings"
date: 2009-11-02
forum: General Help
---

### Post by paulqueen on 2009-11-02
Hi.  

i upgraded my xubuntu to 9.10 thursday... everything working good for the most part, slowly tweaking things over the weekend when i had time, then when i woke up today the clock on my panel said "07:32" and im thinking 'wtf ... it cant be that early' cuz it wasnt that early.  i tried to change it through 'system > time and date' but everytime i would flip the hours ahead manually, about two seconds later it would switch them back.  i unchecked all time servers, tried different time servers, and nothin changed.  hwclock will recognize my universal time as what it should be, but the local time is always 5 hours behind.  i tried reconfigure tzconfig... umm what else... basically ive spent the last 45 minutes sifting through forum posts related to time/date and nothing has helped me yet.

i dont want to have to migrate 5 time zones to the west just to have my laptop be on the correct time, so hopefully some one of ye can help me out.

thx for reading

---

### Post by DeMus on 2009-11-02
> **paulqueen said:**
> Hi.  

i upgraded my xubuntu to 9.10 thursday... everything working good for the most part, slowly tweaking things over the weekend when i had time, then when i woke up today the clock on my panel said "07:32" and im thinking 'wtf ... it cant be that early' cuz it wasnt that early.  i tried to change it through 'system > time and date' but everytime i would flip the hours ahead manually, about two seconds later it would switch them back.  i unchecked all time servers, tried different time servers, and nothin changed.  hwclock will recognize my universal time as what it should be, but the local time is always 5 hours behind.  i tried reconfigure tzconfig... umm what else... basically ive spent the last 45 minutes sifting through forum posts related to time/date and nothing has helped me yet.

i dont want to have to migrate 5 time zones to the west just to have my laptop be on the correct time, so hopefully some one of ye can help me out.

thx for reading

Did you set your time to UTC in Ubuntu?  While in Bios it is not set to UTC? Where do you live and what is your time difference with UTC? Is it 5 hours maybe?

---

### Post by paulqueen on 2009-11-02
> **DeMus said:**
> Did you set your time to UTC in Ubuntu?  While in Bios it is not set to UTC? Where do you live and what is your time difference with UTC? Is it 5 hours maybe?


HA! thanks.  i somehow changed it in the bios. thankies again for the suggestion

---

### Post by P4man on 2009-11-02
Did you change it in the bios, or did you boot windows? Cause windows changes it in the bios, and by default ubuntu does not (or is it vice versa?). Either way a dual boot will keep messing up your time if both ubuntu and windows are set up to synch time with the internet. Easiest solution is to disable UTC for ubuntu

---

