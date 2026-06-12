---
title: "Ubuntu freezes + black screen"
date: 2010-10-05
forum: General Help
---

### Post by inyourhouse on 2010-10-05
Yesterday I transferred my HDD from my Thinkpad T42 to my Thinkpad T41. However, now Ubuntu will randomly (there seems to be no specific trigger) crash. The screen just goes black and all I can see is the cursor, which I can't move. For what it's worth, the black screen with the cursor appears to have a higher resolution than the setting in my user profile. It must be whatever the default resolution is, because the login screen has that resolution too.

I've looked through a few threads on similar issues but they all seem to be related to a problem with Intel drivers. The T41 uses a Radeon RV250 though. I'm still assuming this is some kind of driver problem; the T41 has different components to the T42 I think and would probably need different drivers, but I'm not sure how to go about doing that.

---

### Post by searchfgold6789 on 2010-10-05
The crashing program is either xorg or gdm, for the record.
Ubuntu should install drivers for all new hardware on startup, but that doesn't appear to be happening here for some reason.
There are people trying to do this! Some have trouble with graphics drivers, but [the rest]("http://ubuntuforums.org/showthread.php?t=345084") are fine.
Try getting drivers from the company website and putting them on a cd, installing from there...

---

### Post by inyourhouse on 2010-10-05
I can't find the drivers on the ATI website. Is there any way I can get Ubuntu to remove all current drivers and then get it to install what it thinks I need from scratch?

---

### Post by inyourhouse on 2010-10-05
Something I forgot to mention earlier: when the black screen comes up with the frozen cursor, the caps lock light on flashes on and off. Don't know if that's relevant.

Also, Ubuntu must have recognized the hardware change because running lshw shows that the radeon driver is being used:

```
           *-display
                description: VGA compatible controller
                product: Radeon RV250 [Mobility FireGL 9000]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:11 memory:e0000000-e7ffffff(prefetchable) ioport:3000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff(prefetchable)
```

---

### Post by inyourhouse on 2010-10-05
Okay, I've worked out that a crash only occurs when Transmission is running. I don't know what that could mean. Perhaps a problem with wireless drivers? I looked at syslog, but there was nothing there about the moment of the crash. The last few entries ended over 10 minutes before the crash occurred, but maybe they suggest something. The entries up to 16:10:22 are the end part of the standard startup log entries I think:

```
Oct  5 16:10:21 MJB-Laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Oct  5 16:10:21 MJB-Laptop NetworkManager: <info>  Policy set 'Auto PlusnetWireless' (wlan0) as default for routing and DNS.
Oct  5 16:10:21 MJB-Laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Oct  5 16:10:21 MJB-Laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct  5 16:10:21 MJB-Laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Oct  5 16:10:22 MJB-Laptop ntpdate[2047]: step time server 91.189.94.4 offset 0.529349 sec
Oct  5 16:10:29 MJB-Laptop kernel: [   81.384115] wlan0: no IPv6 routers present
Oct  5 16:11:18 MJB-Laptop AptDaemon: INFO: Initializing daemon
Oct  5 16:12:36 MJB-Laptop kernel: [  208.790709] lo: Disabled Privacy Extensions
Oct  5 16:17:01 MJB-Laptop CRON[2272]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  5 16:17:18 MJB-Laptop AptDaemon: INFO: Quiting due to inactivity
Oct  5 16:17:18 MJB-Laptop AptDaemon: INFO: Shutdown was requested
Oct  5 16:39:01 MJB-Laptop CRON[2343]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct  5 17:09:01 MJB-Laptop CRON[2458]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct  5 17:17:01 MJB-Laptop CRON[2489]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  5 17:19:58 MJB-Laptop anacron[2540]: Anacron 2.3 started on 2010-10-05
Oct  5 17:19:58 MJB-Laptop anacron[2540]: Normal exit (0 jobs run)
```

Then the first few entries after restarting straight after the crash were:

```
Oct  5 17:35:36 MJB-Laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct  5 17:35:36 MJB-Laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="774" x-info="http://www.rsyslog.com"] (re)start
Oct  5 17:35:36 MJB-Laptop rsyslogd: rsyslogd's groupid changed to 102
Oct  5 17:35:36 MJB-Laptop rsyslogd: rsyslogd's userid changed to 101
Oct  5 17:35:36 MJB-Laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct  5 17:35:36 MJB-Laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  5 17:35:36 MJB-Laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  5 17:35:36 MJB-Laptop kernel: [    0.000000] Linux version 2.6.32-25-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
```

Sorry for all the posts, but all of this info may be helpful.

---

