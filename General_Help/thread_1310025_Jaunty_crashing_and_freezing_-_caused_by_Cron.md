---
title: "Jaunty crashing and freezing - caused by Cron?"
date: 2009-11-01
forum: General Help
---

### Post by Tahakki on 2009-11-01
My Jaunty keeps freezing completely, needing hard rebooted, or crashing completely. I look in the system logs, and every time there seems to be these two lines, immediately before the crash/freeze:

```
Oct 24 16:30:02 auterson-study /USR/SBIN/CRON[3952]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

Oct 24 16:40:01 auterson-study /USR/SBIN/CRON[4259]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

I've also been noticing some lines related to pulseaudio. Here are all the lines before what I believe was a freeze:

```
Nov  1 18:40:01 auterson-study console-kit-daemon[2741]: WARNING: Couldn't read /proc/2740/environ: Failed to open file '/proc/2740/environ': No such file or directory 
Nov  1 18:40:01 auterson-study /USR/SBIN/CRON[3401]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov  1 18:43:43 auterson-study anacron[3123]: Job `cron.weekly' started
Nov  1 18:43:43 auterson-study anacron[3628]: Updated timestamp for job `cron.weekly' to 2009-11-01
Nov  1 18:43:50 auterson-study syslogd 1.5.0#5ubuntu3: restart.
Nov  1 18:43:50 auterson-study anacron[3123]: Job `cron.weekly' terminated
Nov  1 18:50:01 auterson-study /USR/SBIN/CRON[3827]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov  1 18:57:18 auterson-study pulseaudio[4273]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Nov  1 18:57:18 auterson-study pulseaudio[4273]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Nov  1 18:57:30 auterson-study x-session-manager[4065]: WARNING: Could not launch application 'awn.desktop': Unable to start application: Failed to execute child process "awn-autostart" (No such file or directory) 
Nov  1 18:57:31 auterson-study pulseaudio[4273]: module-x11-xsmp.c: X11 session manager not running.
Nov  1 18:57:31 auterson-study pulseaudio[4273]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov  1 19:00:01 auterson-study /USR/SBIN/CRON[4496]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Nov  1 19:00:01 auterson-study /USR/SBIN/CRON[4507]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov  1 20:45:25 auterson-study syslogd 1.5.0#5ubuntu3: restart.
```

Any help is massively appreciated. Thanks.

---

### Post by happyhamster on 2009-11-01
- Hello. What's in the /etc/update-motd.d folder?

ls /etc/update-motd.d -l

- Also, which video driver are you using?

---

### Post by Tahakki on 2009-11-01
Output of the command you gave:

```
total 16
lrwxrwxrwx 1 root root   46 2009-04-17 21:04 50-landscape-sysinfo -> /usr/share/landscape/landscape-sysinfo.wrapper
lrwxrwxrwx 1 root root   54 2009-04-17 20:01 90-updates-available -> /usr/lib/update-notifier/update-motd-updates-available
lrwxrwxrwx 1 root root   52 2009-04-17 20:01 99-reboot-required -> /usr/lib/update-notifier/update-motd-reboot-required
drwxr-xr-x 2 root root 4096 2009-05-05 18:32 daily
drwxr-xr-x 2 root root 4096 2009-03-27 08:42 hourly
drwxr-xr-x 2 root root 4096 2009-03-09 05:06 monthly
drwxr-xr-x 2 root root 4096 2009-03-09 05:06 weekly

```

I'm using the nVidia driver 96.43.10.

Thanks.

---

### Post by happyhamster on 2009-11-01
- Can you perhaps trigger a freeze/crash by running update-motd manually? Try running it a few times in a row:

sudo update-motd hourly && sudo update-motd

- Is there any pattern to when a freeze/crash happens? For example heavy CPU load, lot's of RAM in use or such. If so, try to recreate that situation and run above line again.

- Do the crashes/freezes also happen when running an open source video driver (I assume you'll need the nv driver)?

---

### Post by Tahakki on 2009-11-02
I ran the above command as you said, lots of times over while having Google Earth open and the world spinning. Got very slow, but no crash or freeze.

Some situations I noticed the crash:
-Logging in
-Firefox open only
-Running screensaver with nothing else open
-Running Sound Converter

---

### Post by Tahakki on 2009-11-03
Bump'd!

---

