---
title: "NTP using IRIG-B"
date: 2011-06-28
forum: General Help
---

### Post by ManOfKnight on 2011-06-28
I have a Brandywine GPS-8 receiver that is outputting IRIG-B data over a serial cable.  I am attempting to bring this data into Ubuntu 10.04 so that I can have this server share time with the rest of my network.

Problem is, I cannot find ANY information on this at all.  Does anyone have any clue how to complete this task?

I have tried gpsd, it will see something is connected when I do a gpsctl at 9600 baud but I will not see any data behind it.  I know the receiver is connected as I can see six satellites and I have tried two different serial cables.


Thanks,

---

### Post by tgalati4 on 2011-06-28
There was a patch submitted back in 2007 to get that unit to work.  Try 4800 baud:

[https://support.ntp.org/bugs/show_bug.cgi?id=838](https://support.ntp.org/bugs/show_bug.cgi?id=838)

[https://lists.ntp.isc.org/pipermail/hackers/2007-May/002956.html](https://lists.ntp.isc.org/pipermail/hackers/2007-May/002956.html)

Are you setting this up to get accurate GPS time?  If so, it's much simpler to use ntp with 2nd order corrections, using the driftfile--you'll get your network to + or - 1 millisecond of your selected time source servers.

Here's my /etc/ntp.conf:


tgalati4@tubuntu2:/etc$ cat ntp.conf
# Updated 20 Oct 08 to add new servers
logfile /home/tgalati4/ntp_stuff/ntp_trace.log
driftfile /var/lib/ntp/ntp.drift
# The next 4 lines adds statistics to /var/log/ntpstats--hopefully
statistics loopstats peerstats #  clockstats
statsdir /var/log/ntpstats/
filegen peerstats file peers type day link enable
filegen loopstats file loops type day link enable
# filegen clockstats file clockstats type day link enable
server tick.cs.unlv.edu
server tick.mtnlion.com
#server tick.jpunix.net
server ntp1.stsn.net
server north-america.pool.ntp.org
server time.apple.com
# Beef up security policy--see hpubuntu's /etc/ntp.conf
restrict default kod notrap nomodify nopeer noquery
restrict 127.0.0.1 nomodify
broadcast 192.168.1.255

---

