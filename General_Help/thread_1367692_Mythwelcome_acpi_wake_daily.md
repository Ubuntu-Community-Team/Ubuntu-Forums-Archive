---
title: "Mythwelcome acpi wake daily"
date: 2009-12-29
forum: General Help
---

### Post by kempy1000 on 2009-12-29
Hi

I have a mythtv system that turns itself on before a recording and shutsdown after it has finished using acpi wake from this guide (followed word for word):

[http://www.mythtv.org/wiki/ACPI_Wakeup#Integrate_into_mythTV](http://www.mythtv.org/wiki/ACPI_Wakeup#Integrate_into_mythTV)

Now i am trying to get my pc to turn on at 12:00 every day to do a daily system backup.

I couldn't think of a way of doing this until i found the daily wake periods setting in mythwelcome. 

I have changed the settings in mythwelcome to mirror those of the guide mentioned above but the system will not wake at 12:00.
```

Daily wake time is set at 12:00 till 13:00

Wakeup time format: time_t

Command to set Wakeup Time: sudo sh -c "/usr/bin/setwakeup.sh $time" 

```
Instead it wakes when the next recording is scheduled like normal!

Can anyone offer any help?

Thanks
Chris

---

