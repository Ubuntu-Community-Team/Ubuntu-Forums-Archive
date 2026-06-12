---
title: "ntp server not updating time since offset is always 0"
date: 2009-10-08
forum: General Help
---

### Post by dipubu on 2009-10-08
I have installed Ubuntu 9.04, ntp server is running, in /etc/ntp.conf 5 servers are included.

While at bootup the clock is always set correctly, the clock driftes if the computer is running for some time (about 4 minutes a day). If I restart ntp server the clock is smoothly correctly adjusted but after some time it starts drifting again.

When I execute ntpq -p the table with the time servers from /etc/ntp.conf is shown and the value in column "offset" is increasing for each execution (which seems to be correct since the clock is more and more drifting). However, when I execute ntpdc -c loopinfo, the following is displayed:

offset: 0.000000 s 
 frequency: -3,893 ppm 
 poll adjust: 4 
 watchdog timer: 1069 s

 In this output the first three values NEVER change (only immediately after starting ntp server poll adjust is 0 but it quickly switches to 4 and stays there)! With each execution only the watchdog timer increases (which means that the time is never adjusted, as far as I understand). The offset always remains at 0 which is obviously wrong and which may be the reason that the ntp server never thinks about adjusting the time. 

Shouldn't the offset of ntpdc -c loopinfo and of ntpq -p show the same value? Which offset value does the ntp server use (obviously the wrong one displayed by ntpdc - c loopinfo)? Is there a but in ntp or do I have to change somewhere a setting or do I completely missunderstand the whole ntp thing?

 I searched a lot through different forums but did not find any hint. And I don't want to use ntpdate in a cron job (ntpdate works) since in many pages it is explicitly stated that this is a bad idea which could lead to problems and that ntp server is the correct way.

Any help would be very much appreciated.

---

