---
title: "Failure to wake using rtcwake command"
date: 2010-09-20
forum: General Help
---

### Post by GJJ on 2010-09-20
Hi,

I'm trying to wake my ubuntu pc using an rtcwake event and pm-suspend.
I basically use the scripts in this thread: [http://ubuntuforums.org/showthread.php?t=938533](http://ubuntuforums.org/showthread.php?t=938533)

I have by now tried everything I could imagine to get the box to wake up, but it just won't. I have the latest BIOS version and a quite new pc (ASUS M4A78LT-M LE motherboard). The BIOS clock is set to utc, and RTC alarms are enabled there.

Does anyone have any new ideas I could try? I'm pretty surprised I can't get this to work because the same scripts work perfectly on another pc I have (which is actually older).

Any help is greatly appreciated.

Thanks in advance!

---

### Post by dark-triad on 2010-09-23
took alot of playing around but this works for me, not sure if you have already tried it.

```
sudo rtcwake -d rtc0 -m mem -s 40 -u -v
```

---

### Post by GJJ on 2010-09-24
Hi,

Thanks for your reply. Unfortunately, this did not work either.
Here's the output of the command:
```

Using UTC time.
	delta   = 0
	tzone   = 0
	tzname  = UTC
	systime = 1285309982, (UTC) Fri Sep 24 06:33:02 2010
	rtctime = 1285309982, (UTC) Fri Sep 24 06:33:02 2010
alarm 0, sys_time 1285309982, rtc_time 1285309982, seconds 40
rtcwake: wakeup from "mem" using /dev/rtc0 at Fri Sep 24 06:33:43 2010

```

After waiting a couple of minutes, nothing happened and I had to wake it by hand. In the meantime I have found a BIOS setting which let me set a daily wake event. This was actually what I was looking for, so my problem is solved.

Although if there are any other ways this could work, I certainly would be interested.

Thanks for your help!

---

