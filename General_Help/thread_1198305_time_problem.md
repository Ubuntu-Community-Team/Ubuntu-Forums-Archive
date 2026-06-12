---
title: "time problem"
date: 2009-06-27
forum: General Help
---

### Post by plewisfdx on 2009-06-27
The time on my taskbar shows 1:21 PM and its 6:21 PM.

I have Administration->Time and Date set to sync with internet servers. It worked perfectly until this morning.

I am using Chicago as my time setting to get CDT.

Since Chicago right now is UTC -5 is my computer setting the system clock to local but thinking its UTC and subtracting the 5 hours?

Manual settings on the taskbar (right click on clock->Adjust Time and Date->Set system time) returns an error


    ```
Failed to set system time
    /sbin/hwclock returned 256
```



Windows shows the correct time when I boot into vista. 

I installed virtualbox yesterday, would that change a setting? I uninstalled it, and it didn't fix the problem.

The /var/log/messages | grep UTC returns:


    ```
Jun 26 11:52:21 acer-mint kernel: [    1.835629] rtc_cmos 00:04: setting system clock to 2009-06-26 16:51:52 UTC (1246035112)
```


And that UTC time in that line was the correct local time.

The bios clock shows the correct current local time.

I am running Felicia on an Acer Extensa 4420 w/ kernel 2.6.27-14-generic

Administration->Time and Date allows me to change the time to be correct, but is wrong again on reboot.

Thanks for any help.

---

### Post by plewisfdx on 2009-06-27
it looks like its fixed.

The two ntp servers I was using weren't online.  I changed to pool.ntp.org and its fixed.

Not sure why I had the problem in the first place, because I wasn't using ntp before all of this.  My clock was good for months without ntp.

---

