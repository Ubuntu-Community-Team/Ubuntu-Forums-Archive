---
title: "Mail crashed after setting server date/time"
date: 2009-09-26
forum: General Help
---

### Post by redbrad0 on 2009-09-26
Im not sure which command I ran, but I was trying to set the time using a NTP Server and when it kept failing with the error "no server suitable for synchronization found" I ran date 092614212009.00 to force the date/time.

Now when I try to connect to SquirrelMail I get the error "Error connecting to IMAP server: tls://xxx.xxx.xxx.xxx." and my outlook is not able to connect to the IMAP server. 

My first thought is to restart the mail server but I have never done that so I don't have in my records how to restart it but it seems very odd that changing the date/time would cause this. Listed below are all the commands I did run

> root@server01:~# ntpdate pool.ntp.org
26 Sep 14:01:09 ntpdate[28667]: no server suitable for synchronization found
root@server01:~# ntpdate pool.ntp.org
26 Sep 14:12:38 ntpdate[28877]: no server suitable for synchronization found
root@server01:~# /sbin/service ntpd restart
-bash: /sbin/service: No such file or directory
root@server01:~# ntpdate -d ntp.ubuntu.com
26 Sep 14:15:54 ntpdate[28944]: ntpdate 4.2.4p4@1.1520-o Wed May 13 21:09:09 UTC 2009 (1)
transmit(91.189.94.4)
transmit(91.189.94.4)
transmit(91.189.94.4)
transmit(91.189.94.4)
transmit(91.189.94.4)
91.189.94.4: Server dropped: no data
server 91.189.94.4, port 123
stratum 0, precision 0, leap 00, trust 000
refid [91.189.94.4], delay 0.00000, dispersion 64.00000
transmitted 4, in filter 4
reference time:    00000000.00000000  Thu, Feb  7 2036  0:28:16.000
originate timestamp: 00000000.00000000  Thu, Feb  7 2036  0:28:16.000
transmit timestamp:  ce68e6ed.7b0728e9  Sat, Sep 26 2009 14:15:57.480
filter delay:  0.00000  0.00000  0.00000  0.00000
         0.00000  0.00000  0.00000  0.00000
filter offset: 0.000000 0.000000 0.000000 0.000000
         0.000000 0.000000 0.000000 0.000000
delay 0.00000, dispersion 64.00000
offset 0.000000

26 Sep 14:15:58 ntpdate[28944]: no server suitable for synchronization found
root@server01:~# ntpdate -u ntp.ubuntu.com
26 Sep 14:17:20 ntpdate[28962]: no server suitable for synchronization found
root@server01:~# date 092614212009.00
Sat Sep 26 14:21:00 CDT 2009


---

### Post by redbrad0 on 2009-09-26
This has been fixed, basically the mail went offline because the time changed by 4.5 minutes. The command to restart the mail servers is 

/etc/init.d/dovecot restart

---

