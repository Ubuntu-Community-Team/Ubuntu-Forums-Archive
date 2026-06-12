---
title: "RTC &amp; RTCWake problem"
date: 2011-11-24
forum: General Help
---

### Post by tobiz on 2011-11-24
My ubuntu 11.04 system is showing strange behaviour running rtcwake.  If I set the wakeup time in the future then /proc/driver/rtc has the correct time (and the system wakes up correctly).  If I set the wakeup time to some time in the past (reasons explained later) /proc/driver/rtc shows +5min into future from when set. On wake up (by WoL) or re-boot /proc/driver/rtc always shows alrm_time: 00:00:00, alrm_date: 1970-01-01 but, even though this time is in the past the system still wakes up at midnight each day!!!  The reason for trying to set the wake up time in the past was to prevent the issue of it waking up at 00:00:00, but I can't set it in the near past and it seems to wake up anyway even though the date is 1970-01-01!!  The m/b is Jetway JNC98-525, BIOS is AMI version A04.  Thoughts and ideas would be helpful, I'm stumped.

---

### Post by tobiz on 2011-11-25
Problem solved: it was a BIOS setting.

---

