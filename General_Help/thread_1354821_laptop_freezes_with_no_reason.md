---
title: "laptop freezes with no reason?"
date: 2009-12-14
forum: General Help
---

### Post by atomizer on 2009-12-14
Hi 


My laptop freezes almost once a day.
Don't know what is triggering it.
have looked at var/log/messages, but there are no messages from the time it locked down. 

```
Dec 13 23:18:07 tom-laptop kernel: [117019.040088] UDF-fs: Partition marked readonly; forcing readonly mount
Dec 13 23:18:07 tom-laptop kernel: [117019.065643] UDF-fs INFO UDF: Mounting volume '86524_1', timestamp 2006/10/11 18:15 (103c)
Dec 13 23:19:11 tom-laptop pulseaudio[2577]: ratelimit.c: 1 events suppressed
Dec 13 23:25:49 tom-laptop pulseaudio[2577]: ratelimit.c: 1 events suppressed
Dec 13 23:34:45 tom-laptop pulseaudio[2577]: ratelimit.c: 2 events suppressed
Dec 13 23:42:21 tom-laptop pulseaudio[2577]: ratelimit.c: 1 events suppressed
Dec 13 23:42:59 tom-laptop pulseaudio[2577]: ratelimit.c: 2 events suppressed
Dec 13 23:55:15 tom-laptop pulseaudio[2577]: ratelimit.c: 1 events suppressed
Dec 14 00:01:31 tom-laptop pulseaudio[2577]: ratelimit.c: 2 events suppressed
Dec 14 00:36:55 tom-laptop pulseaudio[2577]: ratelimit.c: 1 events suppressed
Dec 14 00:50:25 tom-laptop pulseaudio[2577]: ratelimit.c: 1 events suppressed
Dec 14 00:59:44 tom-laptop pulseaudio[2577]: ratelimit.c: 1 events suppressed
Dec 14 01:11:11 tom-laptop pulseaudio[2577]: ratelimit.c: 1 events suppressed
Dec 14 07:56:50 tom-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="542" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
```

Last time I used it before lockdown was around Dec 14 13:00
I have tested if the screensaver had something to do with it, but that doesn't freeze it.

Please help[HTML][/HTML]

---

### Post by atomizer on 2009-12-15
bump


I had a look at /var/log/syslog after my last freeze (I don't know if the laptop frooze at this point, it always freezes when I'm not around)

```
Dec 15 13:01:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:03:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:03:21 tom-laptop ntpd[12395]: kernel time sync status change 6001
Dec 15 13:05:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:07:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:09:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:11:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:13:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:15:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:17:01 tom-laptop CRON[23046]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 15 13:17:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:19:21 tom-laptop wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Dec 15 13:20:23 tom-laptop ntpd[12395]: kernel time sync status change 2001
```

Has the last message to do with syncing with a time server?
I will stop the syncing and see if the freezing stops.

---

