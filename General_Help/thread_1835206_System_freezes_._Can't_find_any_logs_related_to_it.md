---
title: "System freezes . Can't find any logs related to it."
date: 2011-08-28
forum: General Help
---

### Post by X-jo on 2011-08-28
My system freezes when its either idle downloading torrents or when I am using it. At that time I can't move the cursor and neither does the cap lock button blink. I get to do a Alt Gr + SYSRQ and REISUB.

One instance is when it happened at Aug 28 02:28am. Below are some logs that i found


$ var/log/messages 
```
Aug 27 23:57:49 ajo-Satellite-C640 -- MARK --
Aug 28 00:17:49 ajo-Satellite-C640 -- MARK --
Aug 28 00:37:49 ajo-Satellite-C640 -- MARK --
Aug 28 00:57:49 ajo-Satellite-C640 -- MARK --
Aug 28 01:17:49 ajo-Satellite-C640 -- MARK --
Aug 28 01:37:49 ajo-Satellite-C640 -- MARK --
Aug 28 01:57:49 ajo-Satellite-C640 -- MARK --
Aug 28 02:17:49 ajo-Satellite-C640 -- MARK --
Aug 28 02:31:56 ajo-Satellite-C640 syslogd 1.5.0#6ubuntu1: restart.
Aug 28 02:31:56 ajo-Satellite-C640 kernel: Cannot find map file.
Aug 28 02:31:56 ajo-Satellite-C640 kernel: Loaded 76296 symbols from 54 modules.
Aug 28 02:31:56 ajo-Satellite-C640 kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 28 02:31:56 ajo-Satellite-C640 kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  28 02:31:56 ajo-Satellite-C640 kernel: [    0.000000] Linux version  2.6.38-11-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro  4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 (Ubuntu  2.6.38-11.48-generic 2.6.38.8)
Aug 28 02:31:56 ajo-Satellite-C640  kernel: [    0.000000] Command line:  BOOT_IMAGE=/vmlinuz-2.6.38-11-generic  root=UUID=5438a630-7cc5-4d63-babc-a1b9d983f5fa ro quiet splash  vt.handoff=7
```$ /var/log/syslog.o
```
Aug 28 02:07:14 ajo-Satellite-C640 NetworkManager[829]:  <info> (wlan0): supplicant connection state:  completed ->  group handshake
Aug 28 02:07:14 ajo-Satellite-C640 wpa_supplicant[957]: WPA: Group rekeying completed with c4:3d:c7:9f:7c:fe [GTK=TKIP]
Aug 28 02:07:14 ajo-Satellite-C640 NetworkManager[829]: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 28 02:09:01 ajo-Satellite-C640 CRON[8511]: (root) CMD (  [ -x  /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] &&  find /var/lib/php5/ -depth -mindepth 1 -maxde
pth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Aug 28 02:17:01 ajo-Satellite-C640 CRON[8592]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 02:17:14 ajo-Satellite-C640 NetworkManager[829]: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Aug 28 02:17:14 ajo-Satellite-C640 wpa_supplicant[957]: WPA: Group rekeying completed with c4:3d:c7:9f:7c:fe [GTK=TKIP]
Aug 28 02:17:14 ajo-Satellite-C640 NetworkManager[829]: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 28 02:27:14 ajo-Satellite-C640 NetworkManager[829]: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Aug 28 02:27:14 ajo-Satellite-C640 wpa_supplicant[957]: WPA: Group rekeying completed with c4:3d:c7:9f:7c:fe [GTK=TKIP]
Aug 28 02:27:14 ajo-Satellite-C640 NetworkManager[829]: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 28 02:31:56 ajo-Satellite-C640 syslogd 1.5.0#6ubuntu1: restart.

```Its happened 3-4 times now in the last 5 days.

---

### Post by X-jo on 2011-09-01
this happened again today at 17:19pm

```

[LIST=1]
[*]Sep  1 12:14:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 12:34:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 12:54:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 13:14:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 13:34:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 13:54:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 14:14:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 14:34:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 14:54:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 15:14:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 15:34:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 15:54:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 16:14:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 16:34:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 16:54:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 17:14:44 ajo-Satellite-C640 -- MARK --
[*]Sep  1 17:20:30 ajo-Satellite-C640 kernel: [29124.575319] SysRq : Keyboard mode set to system default
[*]Sep  1 17:21:15 ajo-Satellite-C640 syslogd 1.5.0#6ubuntu1: restart.
[*]Sep  1 17:21:15 ajo-Satellite-C640 kernel: Cannot find map file.
[/LIST]


```

---

### Post by X-jo on 2011-09-02
anyone knows how to get this fixed?

---

### Post by iponeverything on 2011-09-02
What is the history of your issue - someone would have have to be a physic to solve your issue with the information provided. 


- boot the install CD and run a memory test.

---

### Post by X-jo on 2012-01-02
only workaround was to not use wifi and wired connected for internet..

---

### Post by pretty_whistle on 2012-01-02
Freezing?

Have you tried this:
Clean the computer with Bleachbit 1st.  Then power down the computer, pull out the battery if it has one.  Wait 30 seconds, put the battery back in and power it on.

That's it.  I read about this solution in another thread when I had freezes too.  It helped me out.

---

### Post by X-jo on 2012-01-02
> **pretty_whistle said:**
> Freezing?

Have you tried this:
Clean the computer with Bleachbit 1st.  Then power down the computer, pull out the battery if it has one.  Wait 30 seconds, put the battery back in and power it on.

That's it.  I read about this solution in another thread when I had freezes too.  It helped me out.

haven't tried that. the moment i stopped using wifi for internet , the problem went away... i now use a wired connection... i can try that and then test with my fossilized wifi router..

thanks

---

