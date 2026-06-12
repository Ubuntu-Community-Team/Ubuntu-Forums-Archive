---
title: "Screensaver causes laptop to freeze."
date: 2009-11-13
forum: General Help
---

### Post by Sarmacid on 2009-11-13
I have been having problems lately where the screensaver causes the system to freeze, I haven't find a way to reproduce it, it's rather random. I believed gnome-screensaver was causing it, so I switched to xscreensaver but the problem persists. Syslog doesn't provide much information, here are the latest entries before I reboot

```
Nov 13 09:00:02 switch /USR/SBIN/CRON[6913]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Nov 13 09:06:21 switch kernel: [ 3031.843279] SysRq : Keyboard mode set to system default
Nov 13 09:06:22 switch kernel: [ 3032.596407] SysRq : Emergency Sync
Nov 13 09:06:22 switch kernel: [ 3032.599063] Emergency Sync complete
Nov 13 09:06:23 switch exiting on signal 15
Nov 13 09:06:53 switch syslogd 1.5.0#5ubuntu3: restart.
```

Can anyone point me in the right direction to solve this issue?

Also I thought I should mention, I'm using ubuntu 9.04 with gnome.

---

