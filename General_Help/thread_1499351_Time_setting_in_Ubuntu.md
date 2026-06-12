---
title: "Time setting in Ubuntu"
date: 2010-06-01
forum: General Help
---

### Post by Z.K. on 2010-06-01
It seems like every time I install or upgrade Ubuntu the time is off.  This time it was off by 5 hours.  So, I went in and reset the time zone, but I still had to adjust the time manually.  Is there no way to make Ubuntu do this automatically.  It would seem to me that it would just be a matter of retrieving the time from the PC hardware such as the BIOS.  I even tried an Internet time server a few times and that never works.  At least not for me.

:confused:

---

### Post by Jonny87 on 2010-06-01
I have a had a similar problem in the past, perhaps someone can shed abit more light on it than me but it could be that your bios/cmos clock is out. If you haven't already, check it and correct it if it is. If it fixes the problem but the same thing happens again check the bios/cmos clock again. If that's reset again then you may need a new cmos battery.

Like I said though someone may be able to shed more light on it, it may have not be the bios/cmos clock that's problem.

---

### Post by towheedm on 2010-06-01
I dual boot 9.1 and 10.04.  Everytime I boot into 10.04 and then boot into 9.10, 9.10 time moves forward 4 hours.  My time zone is -4 GMT.  In my case I'm sure it's not my CMOS battery.  I think 10.04 is actually setting the CMOS clock without adjusting for the time zone.  Think I'll check this out further.  I thought this was only me.

Also, 10.04 could never seem to find a time server, neither from the default list, nor one that I enter manually.

OK, so I confirmed it.  10.04 is resetting my CMOS clock by +4 hrs.  I did not even have to log in.  Will check to see if a bug on this has been already filed on Launchpad.

---

