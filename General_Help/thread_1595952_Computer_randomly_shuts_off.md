---
title: "Computer randomly shuts off"
date: 2010-10-13
forum: General Help
---

### Post by nuclearj on 2010-10-13
Hello there, this has been going on since I upgraded to 10.04 and it is sooooo annoying.  The computer will just randomly shut off.  Sometimes it will be 10 minutes after turning the computer on, sometimes 10 hours!  Here are my specs:
Motherboard--Gigabyte MA785GM-US2H AMD785G Socket AM2+ MB
Proc.--AMD Athlon II X2 245 2.9Ghz AM3 CPU
Mem-- PNY 1024MB PC6400 DDR2 800Mhz
using onboard video

Also I got this from the messages log when it happens
```
Oct 13 17:53:29 nuclearj-office kernel: [   29.906169] sr 4:0:1:0: [sr0] Add. Sense: Illegal mode for this track
Oct 13 17:53:29 nuclearj-office kernel: [   29.906173] sr 4:0:1:0: [sr0] CDB: Read(10): 28 00 00 03 32 fa 00 00 02 00
Oct 13 17:53:32 nuclearj-office kernel: [   32.770065] UDF-fs: Partition marked readonly; forcing readonly mount
Oct 13 17:53:32 nuclearj-office kernel: [   32.843568] UDF-fs INFO UDF: Mounting volume 'Rosetta Stone V3 - Spanish (La', timestamp 2008/03/20 21:09 (1f10)
Oct 13 17:59:55 nuclearj-office kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 13 17:59:55 nuclearj-office rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="848" x-info="http://www.rsyslog.com"] (re)start
Oct 13 17:59:55 nuclearj-office rsyslogd: rsyslogd's groupid changed to 103
Oct 13 17:59:55 nuclearj-office rsyslogd: rsyslogd's userid changed to 101
Oct 13 17:59:55 nuclearj-office kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 13 17:59:55 nuclearj-office kernel: [    0.000000] Initializing cgroup subsys cpu

```

And this from the syslog
> Oct 13 17:53:35 nuclearj-office kernel: [   35.904018] wlan0: no IPv6 routers present
Oct 13 17:54:24 nuclearj-office AptDaemon: INFO: Initializing daemon
Oct 13 17:59:55 nuclearj-office kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 13 17:59:55 nuclearj-office rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="848" x-info="http://www.rsyslog.com"] (re)start
Oct 13 17:59:55 nuclearj-office rsyslogd: rsyslogd's groupid changed to 103
Oct 13 17:59:55 nuclearj-office rsyslogd: rsyslogd's userid changed to 101
Oct 13 17:59:55 nuclearj-office rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Oct 13 17:59:55 nuclearj-office kernel: [    0.000000] Initializing cgroup subsys cpuset

Could someone point me in a direction to getting this resolved once and for all?

---

### Post by corcomp84 on 2010-10-13
does it seem to still be on.. Because with 10.04 I had a problem with the computer just going to a black screen, but come to find out It was the power settings.. I just change the setting were it said to put the display to sleep, I told it to never put it asleep.. that fixed my problem on about 10 computers.  Its worth a try if you want..

---

### Post by nuclearj on 2010-10-13
> **corcomp84 said:**
> does it seem to still be on.. Because with 10.04 I had a problem with the computer just going to a black screen, but come to find out It was the power settings.. I just change the setting were it said to put the display to sleep, I told it to never put it asleep.. that fixed my problem on about 10 computers.  Its worth a try if you want..

Thanks, I just checked the settings and mine was already set to "never put to sleep"

And yes, the computer seems to still be on... I have to hold the power button to power the computer down; and then press the power button to turn it on again.

---

### Post by nuclearj on 2010-10-13
It just happened again!  Arrrrggggggg.

here is the syslog from when it happened at 19:09:
```

Oct 13 18:08:16 nuclearj-office kernel: [   28.779727] Buffer I/O error on device sr0, logical block 104829
Oct 13 18:08:18 nuclearj-office kernel: [   31.154298] UDF-fs: Partition marked readonly; forcing readonly mount
Oct 13 18:08:18 nuclearj-office kernel: [   31.227942] UDF-fs INFO UDF: Mounting volume 'Rosetta Stone V3 - Spanish (La', timestamp 2008/03/20 21:09 (1f10)
Oct 13 18:08:22 nuclearj-office kernel: [   34.484052] wlan0: no IPv6 routers present
Oct 13 18:09:10 nuclearj-office AptDaemon: INFO: Initializing daemon
Oct 13 18:14:11 nuclearj-office AptDaemon: INFO: Quiting due to inactivity
Oct 13 18:14:11 nuclearj-office AptDaemon: INFO: Shutdown was requested
Oct 13 18:17:01 nuclearj-office CRON[1753]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 13 18:22:20 nuclearj-office wpa_supplicant[1028]: WPA: Group rekeying completed with 00:11:50:9d:ca:68 [GTK=TKIP]
Oct 13 18:22:20 nuclearj-office NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Oct 13 18:22:20 nuclearj-office NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Oct 13 18:37:19 nuclearj-office wpa_supplicant[1028]: WPA: Group rekeying completed with 00:11:50:9d:ca:68 [GTK=TKIP]
Oct 13 18:37:19 nuclearj-office NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Oct 13 18:37:19 nuclearj-office NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Oct 13 18:52:19 nuclearj-office wpa_supplicant[1028]: WPA: Group rekeying completed with 00:11:50:9d:ca:68 [GTK=TKIP]
Oct 13 18:52:19 nuclearj-office NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Oct 13 18:52:19 nuclearj-office NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Oct 13 19:07:18 nuclearj-office wpa_supplicant[1028]: WPA: Group rekeying completed with 00:11:50:9d:ca:68 [GTK=TKIP]
Oct 13 19:07:18 nuclearj-office NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Oct 13 19:07:18 nuclearj-office NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Oct 13 19:10:33 nuclearj-office kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 13 19:10:33 nuclearj-office rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="881" x-info="http://www.rsyslog.com"] (re)start
Oct 13 19:10:33 nuclearj-office rsyslogd: rsyslogd's groupid changed to 103
Oct 13 19:10:33 nuclearj-office rsyslogd: rsyslogd's userid changed to 101
Oct 13 19:10:33 nuclearj-office rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 13 19:10:33 nuclearj-office kernel: [    0.000000] Initializing cgroup subsys cpuset

```

and the msglog from the same time:
```
Oct 13 18:08:16 nuclearj-office kernel: [   28.779708] Info fld=0x332fb
Oct 13 18:08:16 nuclearj-office kernel: [   28.779709] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
Oct 13 18:08:16 nuclearj-office kernel: [   28.779715] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 03 32 fa 00 00 02 00
Oct 13 18:08:18 nuclearj-office kernel: [   31.154298] UDF-fs: Partition marked readonly; forcing readonly mount
Oct 13 18:08:18 nuclearj-office kernel: [   31.227942] UDF-fs INFO UDF: Mounting volume 'Rosetta Stone V3 - Spanish (La', timestamp 2008/03/20 21:09 (1f10)
Oct 13 19:10:33 nuclearj-office kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 13 19:10:33 nuclearj-office rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="881" x-info="http://www.rsyslog.com"] (re)start
Oct 13 19:10:33 nuclearj-office rsyslogd: rsyslogd's groupid changed to 103
Oct 13 19:10:33 nuclearj-office rsyslogd: rsyslogd's userid changed to 101
Oct 13 19:10:33 nuclearj-office kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 13 19:10:33 nuclearj-office kernel: [    0.000000] Initializing cgroup subsys cpu
```

from the syslog, this just happened, I have no idea if it is relevant or not, the computer did not shut down even though it was requested? ```
Oct 13 19:10:52 nuclearj-office kernel: [   36.748061] wlan0: no IPv6 routers present
Oct 13 19:11:40 nuclearj-office AptDaemon: INFO: Initializing daemon
Oct 13 19:16:41 nuclearj-office AptDaemon: INFO: Quiting due to inactivity
Oct 13 19:16:41 nuclearj-office AptDaemon: INFO: Shutdown was requested
Oct 13 19:17:02 nuclearj-office CRON[1845]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Someone please help, this has been going on for 7 months now, and I will be a hero to my wife...

---

### Post by nuclearj on 2010-10-13
ideas anyone?

---

### Post by |{urse on 2010-10-13
Actually having another drink sounds like an amazing idea.

```
Oct 13 17:53:29 nuclearj-office kernel: [   29.906169] sr 4:0:1:0: [sr0] Add. Sense: Illegal mode for this track
Oct 13 17:53:29 nuclearj-office kernel: [   29.906173] sr 4:0:1:0: [sr0] CDB: Read(10): 28 00 00 03 32 fa 00 00 02 00
Oct 13 17:53:32 nuclearj-office kernel: [   32.770065] UDF-fs: Partition marked readonly; forcing readonly mount
Oct 13 17:53:32 nuclearj-office kernel: [   32.843568] UDF-fs INFO UDF: Mounting volume 'Rosetta Stone V3 - Spanish (La', timestamp 2008/03/20 21:09 (1f10)
```

This is all telling you that theres a scratch on the cd-rom in your disk drive.

```
AptDaemon: INFO: Shutdown was requested
```

This is confusing at a glance. All it is saying is that AptDaemon is shutting down.

I'm always suspicious of pny ram. I'd test your memory with the memtest supplied on any ubuntu disk. After that I'd check your hard disk for errors. If all that checks out, I'd be suspicious of acpi bugs or failures.

digging through the output of dmesg | more may reveal the problem also but will more than likely be more trouble than it's worth.

---

### Post by Schrute Farms on 2010-10-13
Have you got Windows installed on the computer?  Try booting into that (shudder) and leave it on for a while, or boot into a live CD version of Ubuntu to try to narrow down if it is a hardware or software problem.  If it keeps dying in a different operating system, then it's probably a hardware problem.

Like |{urse said above, check your memory using memtest.  It also could be a problem with the motherboard.  My desktop was dying randomly, no matter if in Windows or Ubuntu.  Like yours, sometimes it would run for days, sometimes only 10 minutes.  After buying a new power supply, I learned that it was actually the motherboard that finally died.

Good luck!

---

