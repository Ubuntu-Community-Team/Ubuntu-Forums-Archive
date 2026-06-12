---
title: "Is this a problem?"
date: 2010-09-28
forum: General Help
---

### Post by ironhoof on 2010-09-28
I thought I would look through my logs, The startup has been acting strange. It starts and everything works. I don't even get the Ubuntu logo anymore on boot. (Unless its disk checking)

I found this:
Sep 20 23:48:54 ironhoof-sigma pulseaudio[1316]: pid.c: Daemon already running.
Sep 20 23:48:55 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 21 00:06:32 ironhoof-sigma pulseaudio[1281]: ratelimit.c: 3 events suppressed
Sep 21 06:23:06 ironhoof-sigma pulseaudio[1310]: pid.c: Daemon already running.
Sep 21 06:23:07 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 21 23:56:05 ironhoof-sigma pulseaudio[1372]: pid.c: Daemon already running.
Sep 21 23:56:23 ironhoof-sigma pulseaudio[1298]: ratelimit.c: 2 events suppressed
Sep 22 07:52:52 ironhoof-sigma pulseaudio[1363]: pid.c: Daemon already running.
Sep 23 11:41:10 ironhoof-sigma pulseaudio[1363]: pid.c: Daemon already running.
Sep 23 11:43:51 ironhoof-sigma pulseaudio[1282]: ratelimit.c: 2 events suppressed
Sep 23 23:45:45 ironhoof-sigma pulseaudio[1337]: pid.c: Daemon already running.
Sep 23 23:48:37 ironhoof-sigma pulseaudio[1274]: ratelimit.c: 2 events suppressed
Sep 24 11:45:26 ironhoof-sigma pulseaudio[1414]: pid.c: Daemon already running.
Sep 24 12:04:04 ironhoof-sigma pulseaudio[1348]: pid.c: Daemon already running.
Sep 24 12:21:08 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 24 12:21:09 ironhoof-sigma pulseaudio[1383]: pid.c: Daemon already running.
Sep 24 12:21:45 ironhoof-sigma pulseaudio[1302]: ratelimit.c: 4 events suppressed
Sep 24 12:22:25 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 24 12:34:16 ironhoof-sigma pulseaudio[1396]: pid.c: Daemon already running.
Sep 24 12:34:55 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3 events suppressed
Sep 24 12:49:30 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 1857 events suppressed
Sep 24 12:49:35 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4587 events suppressed
Sep 24 12:49:40 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4587 events suppressed
Sep 24 12:49:46 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3849 events suppressed
Sep 24 12:49:51 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4585 events suppressed
Sep 24 12:49:56 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4584 events suppressed
Sep 24 12:50:01 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3854 events suppressed
Sep 24 12:50:06 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4584 events suppressed
Sep 24 12:50:11 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4588 events suppressed
Sep 24 12:50:16 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3852 events suppressed
Sep 24 12:50:21 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4585 events suppressed
Sep 24 12:50:26 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4585 events suppressed
Sep 24 12:50:32 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3851 events suppressed
Sep 24 12:50:37 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4583 events suppressed
Sep 24 12:50:42 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4585 events suppressed
Sep 24 12:50:47 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3852 events suppressed
Sep 24 12:50:52 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4582 events suppressed
Sep 24 12:50:57 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4583 events suppressed
Sep 24 12:51:02 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3854 events suppressed
Sep 24 12:51:07 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4583 events suppressed
Sep 24 12:51:12 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 4585 events suppressed
Sep 24 12:51:18 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3850 events suppressed
Sep 24 12:51:29 ironhoof-sigma pulseaudio[1338]: ratelimit.c: 3718 events suppressed
Sep 24 23:51:12 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 24 23:51:13 ironhoof-sigma pulseaudio[1403]: pid.c: Daemon already running.
Sep 24 23:52:22 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 2 events suppressed
Sep 25 00:57:19 ironhoof-sigma pulseaudio[1386]: pid.c: Daemon already running.
Sep 25 01:49:00 ironhoof-sigma pulseaudio[1372]: pid.c: Daemon already running.
Sep 25 03:35:25 ironhoof-sigma pulseaudio[1288]: ratelimit.c: 1042 events suppressed
Sep 25 03:36:43 ironhoof-sigma pulseaudio[1288]: ratelimit.c: 63 events suppressed
Sep 25 12:23:58 ironhoof-sigma pulseaudio[1378]: pid.c: Daemon already running.
Sep 25 12:24:14 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 2 events suppressed
Sep 25 17:23:43 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 2014 events suppressed
Sep 25 17:23:48 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4588 events suppressed
Sep 25 17:23:53 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4566 events suppressed
Sep 25 17:23:58 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3722 events suppressed
Sep 25 17:24:03 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:24:08 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:24:13 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3857 events suppressed
Sep 25 17:24:18 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:24:23 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4590 events suppressed
Sep 25 17:24:28 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3854 events suppressed
Sep 25 17:24:33 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4585 events suppressed
Sep 25 17:24:38 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:24:44 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3855 events suppressed
Sep 25 17:24:49 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4588 events suppressed
Sep 25 17:24:54 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:24:59 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3850 events suppressed
Sep 25 17:25:04 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:25:09 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4584 events suppressed
Sep 25 17:25:14 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3856 events suppressed
Sep 25 17:25:19 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:25:24 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:25:30 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3853 events suppressed
Sep 25 17:25:35 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:25:40 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:25:45 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3852 events suppressed
Sep 25 17:25:50 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:25:55 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:26:00 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3851 events suppressed
Sep 25 17:26:05 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:26:10 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4588 events suppressed
Sep 25 17:26:16 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3853 events suppressed
Sep 25 17:26:21 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:26:26 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:26:31 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3851 events suppressed
Sep 25 17:26:36 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:26:41 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:26:46 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3854 events suppressed
Sep 25 17:26:51 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4585 events suppressed
Sep 25 17:26:56 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:27:01 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3854 events suppressed
Sep 25 17:27:06 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:27:11 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4588 events suppressed
Sep 25 17:27:17 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3850 events suppressed
Sep 25 17:27:22 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4922 events suppressed
Sep 25 17:27:27 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:27:32 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3852 events suppressed
Sep 25 17:27:37 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4585 events suppressed
Sep 25 17:27:42 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4588 events suppressed
Sep 25 17:27:47 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3851 events suppressed
Sep 25 17:27:52 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4586 events suppressed
Sep 25 17:27:57 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4923 events suppressed
Sep 25 17:28:03 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 3850 events suppressed
Sep 25 17:28:08 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4926 events suppressed
Sep 25 17:28:13 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 4587 events suppressed
Sep 25 17:28:45 ironhoof-sigma pulseaudio[1318]: ratelimit.c: 2325 events suppressed
Sep 25 18:50:45 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 18:52:12 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 18:52:31 ironhoof-sigma pulseaudio[1555]: pid.c: Daemon already running.
Sep 25 18:52:46 ironhoof-sigma pulseaudio[1490]: ratelimit.c: 4 events suppressed
Sep 25 18:54:41 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 18:56:12 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 18:58:11 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 18:58:26 ironhoof-sigma pulseaudio[1520]: pid.c: Daemon already running.
Sep 25 18:59:33 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 19:00:41 ironhoof-sigma pulseaudio[1463]: pid.c: Daemon already running.
Sep 25 19:12:12 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 19:14:11 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 19:21:02 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 19:21:02 ironhoof-sigma pulseaudio[1358]: pid.c: Daemon already running.
Sep 25 19:21:34 ironhoof-sigma pulseaudio[1297]: ratelimit.c: 2 events suppressed
Sep 25 19:22:43 ironhoof-sigma pulseaudio[1348]: pid.c: Daemon already running.
Sep 25 19:33:13 ironhoof-sigma pulseaudio[1334]: pid.c: Daemon already running.
Sep 25 19:43:27 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 19:44:15 ironhoof-sigma pulseaudio[1741]: pid.c: Daemon already running.
Sep 25 19:45:48 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 25 19:45:50 ironhoof-sigma pulseaudio[1460]: pid.c: Daemon already running.
Sep 25 19:46:15 ironhoof-sigma pulseaudio[1328]: ratelimit.c: 2 events suppressed
Sep 26 00:22:16 ironhoof-sigma python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Sep 26 00:22:17 ironhoof-sigma pulseaudio[1328]: pid.c: Daemon already running.

---

### Post by Rubi1200 on 2010-09-28
The log is normal; nothing to be concerned about.

As far as your problem:

What version of Ubuntu are you using and have you added/deleted any partitions/operating systems recently?

---

### Post by ironhoof on 2010-09-30
No, none. I think I figured it out. I installed the PPA for the WACOM repository. I rebooted, and my monitor came up unknown. Then it put me into failsafe mode. I did an old fix by adding an xorg.conf. This locked out my monitor as unknown. I decided to delete the xorg.conf, and well everything came back including the monitor setting, and Ubuntu start up logo. I am still however getting the "Something wicked happened trying to resolve an ubuntu repository (sometimes).", I am assuming this is normal from time to time.

---

