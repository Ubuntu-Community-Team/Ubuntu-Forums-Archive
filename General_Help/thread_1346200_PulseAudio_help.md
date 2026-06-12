---
title: "PulseAudio help?"
date: 2009-12-04
forum: General Help
---

### Post by spongypants23 on 2009-12-04
What will be affected by remove pulseaudio in Karmic?

It seems that it's so integrated in everything nowadays, I don't want to break it.

My reason is because it's been running amok, I believe. I recently had three applications suddenly get killed because I think I ran out of RAM?

Looking through system logs I found this. PA seems to be up to something!

Loooong paste from logs:
```
Dec  4 14:24:13 M1530 pulseaudio[1928]: ratelimit.c: 18 events suppressed
Dec  4 14:24:20 M1530 pulseaudio[1928]: ratelimit.c: 59 events suppressed
Dec  4 14:24:25 M1530 pulseaudio[1928]: ratelimit.c: 204 events suppressed
Dec  4 14:24:31 M1530 pulseaudio[1928]: ratelimit.c: 63 events suppressed
Dec  4 14:24:54 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 14:25:01 M1530 pulseaudio[1928]: ratelimit.c: 86 events suppressed
Dec  4 14:25:06 M1530 pulseaudio[1928]: ratelimit.c: 137 events suppressed
Dec  4 14:25:12 M1530 pulseaudio[1928]: ratelimit.c: 236 events suppressed
Dec  4 14:25:17 M1530 pulseaudio[1928]: ratelimit.c: 235 events suppressed
Dec  4 14:25:23 M1530 pulseaudio[1928]: ratelimit.c: 397 events suppressed
Dec  4 14:25:28 M1530 pulseaudio[1928]: ratelimit.c: 140 events suppressed
Dec  4 14:25:33 M1530 pulseaudio[1928]: ratelimit.c: 56 events suppressed
Dec  4 14:25:43 M1530 pulseaudio[1928]: ratelimit.c: 263 events suppressed
Dec  4 14:25:53 M1530 pulseaudio[1928]: ratelimit.c: 141 events suppressed
Dec  4 14:25:59 M1530 pulseaudio[1928]: ratelimit.c: 70 events suppressed
Dec  4 14:26:05 M1530 pulseaudio[1928]: ratelimit.c: 68 events suppressed
Dec  4 14:26:11 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 14:28:01 M1530 pulseaudio[1928]: ratelimit.c: 75 events suppressed
Dec  4 14:28:05 M1530 kernel: [ 2633.419309] CE: hpet increasing min_delta_ns to 33750 nsec
Dec  4 14:28:34 M1530 pulseaudio[1928]: ratelimit.c: 64 events suppressed
Dec  4 14:28:39 M1530 pulseaudio[1928]: ratelimit.c: 304 events suppressed
Dec  4 14:28:45 M1530 pulseaudio[1928]: ratelimit.c: 78 events suppressed
Dec  4 14:28:56 M1530 pulseaudio[1928]: ratelimit.c: 12 events suppressed
Dec  4 14:29:02 M1530 pulseaudio[1928]: ratelimit.c: 15 events suppressed
Dec  4 14:29:08 M1530 pulseaudio[1928]: ratelimit.c: 14 events suppressed
Dec  4 14:29:47 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 14:30:28 M1530 pulseaudio[1928]: ratelimit.c: 15 events suppressed
Dec  4 14:30:33 M1530 pulseaudio[1928]: ratelimit.c: 14 events suppressed
Dec  4 14:30:39 M1530 pulseaudio[1928]: ratelimit.c: 15 events suppressed
Dec  4 14:30:45 M1530 pulseaudio[1928]: ratelimit.c: 12 events suppressed
Dec  4 14:30:50 M1530 pulseaudio[1928]: ratelimit.c: 35 events suppressed
Dec  4 14:30:55 M1530 pulseaudio[1928]: ratelimit.c: 104 events suppressed
Dec  4 14:31:00 M1530 pulseaudio[1928]: ratelimit.c: 100 events suppressed
Dec  4 14:31:14 M1530 pulseaudio[1928]: ratelimit.c: 58 events suppressed
Dec  4 14:31:22 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 14:31:27 M1530 pulseaudio[1928]: ratelimit.c: 284 events suppressed
Dec  4 14:31:32 M1530 pulseaudio[1928]: ratelimit.c: 80 events suppressed
Dec  4 14:31:43 M1530 pulseaudio[1928]: ratelimit.c: 283 events suppressed
Dec  4 14:31:49 M1530 pulseaudio[1928]: ratelimit.c: 25 events suppressed
Dec  4 14:32:20 M1530 pulseaudio[1928]: ratelimit.c: 20 events suppressed
Dec  4 14:32:26 M1530 pulseaudio[1928]: ratelimit.c: 370 events suppressed
Dec  4 14:32:31 M1530 pulseaudio[1928]: ratelimit.c: 104 events suppressed
Dec  4 14:58:37 M1530 gnome-screensaver-dialog: pam_sm_authenticate: Called
Dec  4 14:58:37 M1530 gnome-screensaver-dialog: pam_sm_authenticate: username = [simon]
Dec  4 15:02:55 M1530 pulseaudio[1928]: ratelimit.c: 97 events suppressed
Dec  4 15:03:07 M1530 pulseaudio[1928]: ratelimit.c: 16 events suppressed
Dec  4 15:03:13 M1530 pulseaudio[1928]: ratelimit.c: 116 events suppressed
Dec  4 15:03:18 M1530 pulseaudio[1928]: ratelimit.c: 201 events suppressed
Dec  4 15:03:24 M1530 pulseaudio[1928]: ratelimit.c: 115 events suppressed
Dec  4 15:03:29 M1530 pulseaudio[1928]: ratelimit.c: 368 events suppressed
Dec  4 15:03:34 M1530 pulseaudio[1928]: ratelimit.c: 189 events suppressed
Dec  4 15:03:42 M1530 pulseaudio[1928]: ratelimit.c: 292 events suppressed
Dec  4 15:03:53 M1530 pulseaudio[1928]: ratelimit.c: 182 events suppressed
Dec  4 15:03:58 M1530 pulseaudio[1928]: ratelimit.c: 104 events suppressed
Dec  4 15:04:04 M1530 pulseaudio[1928]: ratelimit.c: 180 events suppressed
Dec  4 15:04:09 M1530 pulseaudio[1928]: ratelimit.c: 217 events suppressed
Dec  4 15:04:14 M1530 pulseaudio[1928]: ratelimit.c: 179 events suppressed
Dec  4 15:04:19 M1530 pulseaudio[1928]: ratelimit.c: 115 events suppressed
Dec  4 15:04:24 M1530 pulseaudio[1928]: ratelimit.c: 89 events suppressed
Dec  4 15:04:35 M1530 pulseaudio[1928]: ratelimit.c: 179 events suppressed
Dec  4 15:04:46 M1530 pulseaudio[1928]: ratelimit.c: 289 events suppressed
Dec  4 15:04:51 M1530 pulseaudio[1928]: ratelimit.c: 103 events suppressed
Dec  4 15:04:56 M1530 pulseaudio[1928]: ratelimit.c: 97 events suppressed
Dec  4 15:05:14 M1530 pulseaudio[1928]: ratelimit.c: 171 events suppressed
Dec  4 15:06:06 M1530 pulseaudio[1928]: ratelimit.c: 72 events suppressed
Dec  4 15:06:11 M1530 pulseaudio[1928]: ratelimit.c: 123 events suppressed
Dec  4 15:06:16 M1530 pulseaudio[1928]: ratelimit.c: 145 events suppressed
Dec  4 15:06:27 M1530 pulseaudio[1928]: ratelimit.c: 771 events suppressed
Dec  4 15:06:32 M1530 pulseaudio[1928]: ratelimit.c: 2558 events suppressed
Dec  4 15:06:37 M1530 pulseaudio[1928]: ratelimit.c: 2303 events suppressed
Dec  4 15:06:42 M1530 pulseaudio[1928]: ratelimit.c: 2471 events suppressed
Dec  4 15:06:47 M1530 pulseaudio[1928]: ratelimit.c: 2175 events suppressed
Dec  4 15:06:52 M1530 pulseaudio[1928]: ratelimit.c: 2265 events suppressed
Dec  4 15:06:57 M1530 pulseaudio[1928]: ratelimit.c: 2443 events suppressed
Dec  4 15:07:03 M1530 pulseaudio[1928]: ratelimit.c: 825 events suppressed
Dec  4 15:07:09 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 15:07:22 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:07:35 M1530 pulseaudio[1928]: ratelimit.c: 76 events suppressed
Dec  4 15:07:53 M1530 pulseaudio[1928]: ratelimit.c: 267 events suppressed
Dec  4 15:08:00 M1530 pulseaudio[1928]: ratelimit.c: 45 events suppressed
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:10 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:08:15 M1530 pulseaudio[1928]: ratelimit.c: 46 events suppressed
Dec  4 15:08:23 M1530 pulseaudio[1928]: ratelimit.c: 224 events suppressed
Dec  4 15:08:37 M1530 pulseaudio[1928]: ratelimit.c: 155 events suppressed
Dec  4 15:08:42 M1530 pulseaudio[1928]: ratelimit.c: 109 events suppressed
Dec  4 15:08:47 M1530 pulseaudio[1928]: ratelimit.c: 209 events suppressed
Dec  4 15:08:54 M1530 pulseaudio[1928]: ratelimit.c: 81 events suppressed
Dec  4 15:09:00 M1530 pulseaudio[1928]: ratelimit.c: 160 events suppressed
Dec  4 15:09:20 M1530 pulseaudio[1928]: ratelimit.c: 20 events suppressed
Dec  4 15:09:26 M1530 pulseaudio[1928]: ratelimit.c: 161 events suppressed
Dec  4 15:09:38 M1530 pulseaudio[1928]: ratelimit.c: 164 events suppressed
Dec  4 15:09:44 M1530 pulseaudio[1928]: ratelimit.c: 49 events suppressed
Dec  4 15:09:49 M1530 pulseaudio[1928]: ratelimit.c: 263 events suppressed
Dec  4 15:09:56 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 15:10:01 M1530 pulseaudio[1928]: ratelimit.c: 412 events suppressed
Dec  4 15:10:06 M1530 pulseaudio[1928]: ratelimit.c: 1089 events suppressed
Dec  4 15:10:12 M1530 pulseaudio[1928]: ratelimit.c: 160 events suppressed
Dec  4 15:10:17 M1530 pulseaudio[1928]: ratelimit.c: 68 events suppressed
Dec  4 15:10:24 M1530 pulseaudio[1928]: asyncq.c: q overrun, queuing locally
Dec  4 15:10:30 M1530 pulseaudio[1928]: ratelimit.c: 212 events suppressed
Dec  4 15:10:35 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 15:10:40 M1530 pulseaudio[1928]: ratelimit.c: 197 events suppressed
Dec  4 15:10:51 M1530 pulseaudio[1928]: ratelimit.c: 191 events suppressed
Dec  4 15:10:56 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 15:11:06 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 15:11:11 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 15:11:16 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 15:12:47 M1530 pulseaudio[1928]: ratelimit.c: 214 events suppressed
Dec  4 15:13:03 M1530 pulseaudio[1928]: ratelimit.c: 22 events suppressed
Dec  4 15:13:09 M1530 pulseaudio[1928]: ratelimit.c: 133 events suppressed
Dec  4 15:13:15 M1530 pulseaudio[1928]: ratelimit.c: 116 events suppressed
Dec  4 15:13:20 M1530 pulseaudio[1928]: ratelimit.c: 165 events suppressed
Dec  4 15:13:25 M1530 pulseaudio[1928]: ratelimit.c: 29 events suppressed
Dec  4 15:13:40 M1530 pulseaudio[1928]: ratelimit.c: 42 events suppressed
Dec  4 15:13:51 M1530 pulseaudio[1928]: ratelimit.c: 127 events suppressed
Dec  4 15:13:57 M1530 pulseaudio[1928]: ratelimit.c: 176 events suppressed
Dec  4 15:14:08 M1530 pulseaudio[1928]: ratelimit.c: 147 events suppressed
Dec  4 15:14:14 M1530 pulseaudio[1928]: ratelimit.c: 215 events suppressed
Dec  4 15:14:27 M1530 pulseaudio[1928]: ratelimit.c: 11 events suppressed
Dec  4 15:14:32 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 15:14:38 M1530 pulseaudio[1928]: ratelimit.c: 407 events suppressed
Dec  4 15:14:44 M1530 pulseaudio[1928]: ratelimit.c: 230 events suppressed
Dec  4 15:14:50 M1530 pulseaudio[1928]: ratelimit.c: 25 events suppressed
Dec  4 15:14:57 M1530 pulseaudio[1928]: ratelimit.c: 166 events suppressed
Dec  4 15:15:02 M1530 pulseaudio[1928]: ratelimit.c: 151 events suppressed
Dec  4 15:15:10 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 15:15:16 M1530 pulseaudio[1928]: ratelimit.c: 238 events suppressed
Dec  4 15:15:29 M1530 pulseaudio[1928]: ratelimit.c: 13 events suppressed
Dec  4 15:15:48 M1530 pulseaudio[1928]: ratelimit.c: 71 events suppressed
Dec  4 15:15:53 M1530 pulseaudio[1928]: ratelimit.c: 89 events suppressed
Dec  4 15:16:00 M1530 pulseaudio[1928]: ratelimit.c: 39 events suppressed
Dec  4 15:16:06 M1530 pulseaudio[1928]: ratelimit.c: 51 events suppressed
Dec  4 15:16:24 M1530 pulseaudio[1928]: ratelimit.c: 22 events suppressed
Dec  4 15:16:50 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:17:01 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:17:12 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 15:17:17 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 15:18:08 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:18:13 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 15:18:39 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 15:19:03 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 15:19:09 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:19:21 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 15:21:04 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:23:12 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:25:20 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:26:17 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:26:38 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 15:31:07 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:31:18 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 15:31:34 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:32:17 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 15:32:22 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 15:32:29 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 15:32:48 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 15:33:32 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:33:42 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:35:13 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:36:09 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:36:39 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 15:39:59 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:40:45 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 15:42:17 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 15:46:17 M1530 sudo: pam_sm_authenticate: Called
Dec  4 15:46:17 M1530 sudo: pam_sm_authenticate: username = [simon]
Dec  4 15:47:29 M1530 sudo: pam_sm_authenticate: Called
Dec  4 15:47:29 M1530 sudo: pam_sm_authenticate: username = [simon]
Dec  4 15:51:04 M1530 kernel: [ 7612.110169] vboxdrv: fAsync=0 offMin=0x198 offMax=0xffc
Dec  4 15:51:04 M1530 kernel: [ 7612.110214] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Dec  4 15:52:03 M1530 kernel: [ 7671.566341] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Dec  4 17:05:18 M1530 gnome-screensaver-dialog: pam_sm_authenticate: Called
Dec  4 17:05:18 M1530 gnome-screensaver-dialog: pam_sm_authenticate: username = [simon]
Dec  4 17:09:03 M1530 gnome-screensaver-dialog: pam_sm_authenticate: Called
Dec  4 17:09:03 M1530 gnome-screensaver-dialog: pam_sm_authenticate: username = [simon]
Dec  4 17:29:05 M1530 gnome-screensaver-dialog: pam_sm_authenticate: Called
Dec  4 17:29:05 M1530 gnome-screensaver-dialog: pam_sm_authenticate: username = [simon]
Dec  4 17:48:04 M1530 pulseaudio[1928]: ratelimit.c: 10 events suppressed
Dec  4 17:48:19 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 17:48:25 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:48:30 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:48:50 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 17:48:56 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 17:49:12 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 17:49:17 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:49:22 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 17:49:28 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 17:49:39 M1530 pulseaudio[1928]: ratelimit.c: 14 events suppressed
Dec  4 17:49:44 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 17:49:49 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:49:59 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 17:50:10 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:50:15 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 17:50:21 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 17:50:31 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 17:50:37 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:50:42 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:50:47 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 17:50:52 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 17:50:57 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 17:51:02 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 17:51:08 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 17:51:14 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:51:19 M1530 pulseaudio[1928]: ratelimit.c: 19 events suppressed
Dec  4 17:51:24 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:51:30 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 17:51:46 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:51:52 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 17:51:57 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:52:07 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 17:52:12 M1530 pulseaudio[1928]: ratelimit.c: 19 events suppressed
Dec  4 17:52:17 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 17:52:23 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:52:52 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:53:31 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:53:53 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 17:54:03 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:54:08 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:54:13 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 17:54:25 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 17:54:45 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:54:51 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 17:54:56 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:55:01 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 17:55:06 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 17:55:11 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:55:16 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 17:55:21 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 17:55:26 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 17:55:32 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:55:37 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 17:55:42 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:55:47 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 17:55:52 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 17:55:57 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 17:56:03 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:56:08 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 17:56:30 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 17:56:35 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:56:41 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:56:46 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 17:56:52 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:56:57 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 17:57:02 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:57:07 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 17:57:12 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 17:57:28 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:57:44 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 17:58:07 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 17:58:17 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:00:16 M1530 sudo: pam_sm_authenticate: Called
Dec  4 18:00:16 M1530 sudo: pam_sm_authenticate: username = [simon]
Dec  4 18:04:12 M1530 pulseaudio[1928]: ratelimit.c: 75 events suppressed
Dec  4 18:04:17 M1530 pulseaudio[1928]: ratelimit.c: 142 events suppressed
Dec  4 18:04:27 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:04:32 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:04:37 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:04:43 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:04:48 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:04:53 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:04:59 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 18:05:22 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 18:05:28 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:05:38 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 18:05:49 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:06:04 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 18:06:09 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:06:20 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:06:36 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:06:41 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 18:06:52 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:07:04 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:07:43 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:07:53 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 18:07:58 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 18:08:04 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 18:08:09 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:08:14 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 18:08:19 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:08:34 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:08:46 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 18:08:51 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:09:02 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:09:08 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:09:13 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:09:36 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:09:41 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:09:56 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:10:07 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 18:10:17 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 18:10:23 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 18:10:28 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:10:33 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:10:43 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:10:54 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 18:11:04 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 18:11:09 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 18:11:14 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 18:11:19 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:11:24 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:11:29 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 18:11:45 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 18:11:50 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 18:14:46 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 18:14:52 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 18:14:57 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 18:42:27 M1530 sudo: pam_sm_authenticate: Called
Dec  4 18:42:27 M1530 sudo: pam_sm_authenticate: username = [simon]
Dec  4 19:00:46 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 19:07:44 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 19:30:14 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:39:34 M1530 pulseaudio[1928]: ratelimit.c: 52 events suppressed
Dec  4 20:39:39 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:39:44 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:39:50 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:40:00 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 20:40:22 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:40:27 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:40:37 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 20:40:42 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 20:40:48 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 20:40:54 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:40:59 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:41:14 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:41:20 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:41:30 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:41:40 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:41:46 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 20:41:51 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:42:02 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:42:07 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:42:12 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:42:17 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:42:22 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:42:27 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:42:33 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:42:43 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:42:48 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:42:58 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:43:15 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:43:20 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:43:25 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:43:30 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:43:35 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:43:40 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 20:44:01 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:44:11 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:44:28 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:44:33 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:44:38 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:44:43 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 20:44:48 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:45:04 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:45:20 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:45:25 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 20:45:30 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:45:35 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:45:40 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:45:46 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:45:51 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:45:57 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:46:07 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:46:12 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:46:23 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:46:28 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:46:33 M1530 pulseaudio[1928]: ratelimit.c: 10 events suppressed
Dec  4 20:46:38 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:46:44 M1530 pulseaudio[1928]: ratelimit.c: 16 events suppressed
Dec  4 20:46:55 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:47:00 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:47:06 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 20:47:11 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:47:16 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:47:26 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:47:31 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 20:47:36 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:47:42 M1530 pulseaudio[1928]: ratelimit.c: 11 events suppressed
Dec  4 20:47:47 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:47:52 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:47:57 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:48:02 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:48:08 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:48:18 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:48:23 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 20:48:29 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:48:40 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 20:48:51 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:48:56 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:49:06 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:49:16 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:49:21 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:49:27 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 20:49:32 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:49:42 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:49:48 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:49:58 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 20:50:03 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:50:08 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:50:19 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:50:29 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:50:34 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:50:49 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:50:55 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:51:00 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:51:05 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:51:10 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:51:25 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:51:41 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 20:51:57 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:52:13 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:52:18 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:52:29 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:52:34 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:52:51 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:52:56 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:53:01 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 20:53:07 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:53:12 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:53:17 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 20:53:22 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:53:27 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:53:33 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 20:53:38 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:53:49 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:54:04 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:54:09 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:54:14 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 20:54:29 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:54:34 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:54:45 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:54:50 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:54:57 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:55:04 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:55:09 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:55:14 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:55:20 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 20:55:25 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:55:30 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:55:35 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:55:51 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  4 20:56:06 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:56:22 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:56:27 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:56:37 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:56:42 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:56:53 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 20:56:58 M1530 pulseaudio[1928]: ratelimit.c: 8 events suppressed
Dec  4 20:57:03 M1530 pulseaudio[1928]: ratelimit.c: 9 events suppressed
Dec  4 20:57:14 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:57:20 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:57:26 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:57:32 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:57:42 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:57:57 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:58:03 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:58:08 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:58:13 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:58:18 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 20:58:24 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:58:29 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:58:39 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:58:44 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:58:49 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:58:55 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 20:59:05 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  4 20:59:10 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 20:59:15 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 20:59:20 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:59:30 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  4 20:59:36 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 20:59:41 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 21:00:02 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  4 21:00:10 M1530 gnome-screensaver-dialog: pam_sm_authenticate: Called
Dec  4 21:00:10 M1530 gnome-screensaver-dialog: pam_sm_authenticate: username = [simon]
Dec  4 21:01:04 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 21:01:25 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 21:01:46 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 21:02:33 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 21:03:58 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 21:28:42 M1530 gnome-screensaver-dialog: pam_sm_authenticate: Called
Dec  4 21:28:42 M1530 gnome-screensaver-dialog: pam_sm_authenticate: username = [simon]
Dec  4 23:20:51 M1530 kernel: [34599.144187] usb 5-1: USB disconnect, address 2
Dec  4 23:33:20 M1530 kernel: [35347.841137] usb 5-1: new low speed USB device using uhci_hcd and address 3
Dec  4 23:33:20 M1530 kernel: [35348.013326] usb 5-1: configuration #1 chosen from 1 choice
Dec  4 23:33:20 M1530 kernel: [35348.036219] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input17
Dec  4 23:33:20 M1530 kernel: [35348.036427] generic-usb 0003:046D:C404.0004: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.0-1/input0
Dec  4 23:33:20 M1530 kernel: [35348.454109] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Dec  4 23:54:13 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  4 23:56:05 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  4 23:57:57 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  4 23:58:35 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 00:02:31 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:06:34 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:16:35 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 00:16:40 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:17:24 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:22:10 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  5 00:22:27 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:22:52 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:23:04 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:23:09 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  5 00:23:15 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:23:35 M1530 sudo: pam_sm_authenticate: Called
Dec  5 00:23:35 M1530 sudo: pam_sm_authenticate: username = [simon]
Dec  5 00:23:41 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:24:13 M1530 pulseaudio[1928]: ratelimit.c: 5 events suppressed
Dec  5 00:24:32 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  5 00:24:37 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:24:56 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 00:29:14 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  5 00:31:05 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  5 00:31:47 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:32:33 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 00:34:41 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:34:46 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  5 00:35:07 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:38:20 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:38:57 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:40:31 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  5 00:40:42 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:41:38 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:43:47 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:43:59 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  5 00:45:33 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 00:47:00 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:49:06 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:50:02 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:50:07 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 00:50:50 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:50:56 M1530 pulseaudio[1928]: ratelimit.c: 6 events suppressed
Dec  5 00:51:14 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 00:51:27 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:53:31 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:53:38 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:55:13 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:55:35 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 00:56:59 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 00:58:45 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 01:01:14 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 01:01:42 M1530 pulseaudio[1928]: ratelimit.c: 3 events suppressed
Dec  5 01:02:27 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 01:05:51 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 01:07:09 M1530 kernel: [40976.598404] SLVoice: page allocation failure. order:2, mode:0x4020
Dec  5 01:07:09 M1530 kernel: [40976.598409] Pid: 16447, comm: SLVoice Tainted: P           2.6.31-15-generic-pae #50-Ubuntu
Dec  5 01:07:09 M1530 kernel: [40976.598411] Call Trace:
Dec  5 01:07:09 M1530 kernel: [40976.598418]  [<c05747ae>] ? printk+0x18/0x1a
Dec  5 01:07:09 M1530 kernel: [40976.598424]  [<c01ba2c0>] __alloc_pages_slowpath+0x340/0x480
Dec  5 01:07:09 M1530 kernel: [40976.598427]  [<c01ba50f>] __alloc_pages_nodemask+0x10f/0x120
Dec  5 01:07:09 M1530 kernel: [40976.598430]  [<c01ba567>] __get_free_pages+0x17/0x30
Dec  5 01:07:09 M1530 kernel: [40976.598434]  [<c01e3ed8>] __kmalloc_track_caller+0xd8/0x180
Dec  5 01:07:09 M1530 kernel: [40976.598449]  [<f837f278>] ? iwl_pass_packet_to_mac80211+0xe8/0x210 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.598458]  [<f837f843>] ? iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.598462]  [<c04998ed>] __alloc_skb+0x4d/0x130
Dec  5 01:07:09 M1530 kernel: [40976.598470]  [<f837f843>] iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.598479]  [<f8380a90>] iwl_rx_replenish_now+0x10/0x20 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.598486]  [<f853dafd>] iwl_rx_handle+0x20d/0x290 [iwlagn]
Dec  5 01:07:09 M1530 kernel: [40976.598489]  [<c04988bb>] ? skb_dequeue+0x4b/0x70
Dec  5 01:07:09 M1530 kernel: [40976.598495]  [<f853dd3d>] iwl_irq_tasklet_legacy+0x1bd/0x3c0 [iwlagn]
Dec  5 01:07:09 M1530 kernel: [40976.598500]  [<c0318e16>] ? rb_insert_color+0x76/0x100
Dec  5 01:07:09 M1530 kernel: [40976.598504]  [<c014baa7>] tasklet_action+0xa7/0xc0
Dec  5 01:07:09 M1530 kernel: [40976.598507]  [<c014cc40>] __do_softirq+0x90/0x1a0
Dec  5 01:07:09 M1530 kernel: [40976.598510]  [<c019186c>] ? handle_IRQ_event+0x4c/0x140
Dec  5 01:07:09 M1530 kernel: [40976.598513]  [<c0194514>] ? move_native_irq+0x14/0x50
Dec  5 01:07:09 M1530 kernel: [40976.598516]  [<c014cd8d>] do_softirq+0x3d/0x40
Dec  5 01:07:09 M1530 kernel: [40976.598519]  [<c014cecd>] irq_exit+0x5d/0x70
Dec  5 01:07:09 M1530 kernel: [40976.598522]  [<c0104f10>] do_IRQ+0x50/0xc0
Dec  5 01:07:09 M1530 kernel: [40976.598526]  [<c01711bc>] ? generic_smp_call_function_single_interrupt+0x7c/0x90
Dec  5 01:07:09 M1530 kernel: [40976.598529]  [<c01039b0>] common_interrupt+0x30/0x40
Dec  5 01:07:09 M1530 kernel: [40976.598531] Mem-Info:
Dec  5 01:07:09 M1530 kernel: [40976.598533] DMA per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.598535] CPU    0: hi:    0, btch:   1 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.598536] CPU    1: hi:    0, btch:   1 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.598538] Normal per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.598539] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.598541] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.598542] HighMem per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.598544] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.598545] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.598549] Active_anon:414711 active_file:90616 inactive_anon:92277
Dec  5 01:07:09 M1530 kernel: [40976.598549]  inactive_file:95990 unevictable:79020 dirty:2 writeback:25 unstable:0
Dec  5 01:07:09 M1530 kernel: [40976.598551]  free:108218 slab:12488 mapped:104190 pagetables:3108 bounce:0
Dec  5 01:07:09 M1530 kernel: [40976.598554] DMA free:3476kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:24kB inactive_file:16kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.598557] lowmem_reserve[]: 0 867 4042 4042
Dec  5 01:07:09 M1530 kernel: [40976.598562] Normal free:4208kB min:3732kB low:4664kB high:5596kB active_anon:46428kB inactive_anon:46308kB active_file:740kB inactive_file:436kB unevictable:316080kB present:887976kB pages_scanned:193 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.598565] lowmem_reserve[]: 0 0 25403 25403
Dec  5 01:07:09 M1530 kernel: [40976.598570] HighMem free:425188kB min:512kB low:3928kB high:7344kB active_anon:1612416kB inactive_anon:322800kB active_file:361700kB inactive_file:383508kB unevictable:0kB present:3251612kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.598572] lowmem_reserve[]: 0 0 0 0
Dec  5 01:07:09 M1530 kernel: [40976.598576] DMA: 3*4kB 5*8kB 2*16kB 4*32kB 1*64kB 3*128kB 3*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3476kB
Dec  5 01:07:09 M1530 kernel: [40976.598585] Normal: 842*4kB 61*8kB 0*16kB 1*32kB 0*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4144kB
Dec  5 01:07:09 M1530 kernel: [40976.598593] HighMem: 30609*4kB 17484*8kB 7606*16kB 1079*32kB 90*64kB 7*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 425188kB
Dec  5 01:07:09 M1530 kernel: [40976.598602] 215485 total pagecache pages
Dec  5 01:07:09 M1530 kernel: [40976.598604] 8627 pages in swap cache
Dec  5 01:07:09 M1530 kernel: [40976.598605] Swap cache stats: add 119723, delete 111096, find 4720/6252
Dec  5 01:07:09 M1530 kernel: [40976.598607] Free swap  = 7895004kB
Dec  5 01:07:09 M1530 kernel: [40976.598609] Total swap = 8000360kB
Dec  5 01:07:09 M1530 kernel: [40976.600004] 1179648 pages RAM
Dec  5 01:07:09 M1530 kernel: [40976.600004] 951810 pages HighMem
Dec  5 01:07:09 M1530 kernel: [40976.600004] 186328 pages reserved
Dec  5 01:07:09 M1530 kernel: [40976.600004] 489196 pages shared
Dec  5 01:07:09 M1530 kernel: [40976.600004] 502013 pages non-shared
Dec  5 01:07:09 M1530 kernel: [40976.600004] SLVoice: page allocation failure. order:2, mode:0x4020
Dec  5 01:07:09 M1530 kernel: [40976.600004] Pid: 16447, comm: SLVoice Tainted: P           2.6.31-15-generic-pae #50-Ubuntu
Dec  5 01:07:09 M1530 kernel: [40976.600004] Call Trace:
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c05747ae>] ? printk+0x18/0x1a
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c01ba2c0>] __alloc_pages_slowpath+0x340/0x480
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c01ba50f>] __alloc_pages_nodemask+0x10f/0x120
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c01ba567>] __get_free_pages+0x17/0x30
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c01e3ed8>] __kmalloc_track_caller+0xd8/0x180
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<f837f278>] ? iwl_pass_packet_to_mac80211+0xe8/0x210 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<f837f843>] ? iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c04998ed>] __alloc_skb+0x4d/0x130
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<f837f843>] iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<f8380a51>] ? iwl_rx_queue_restock+0x111/0x140 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<f8380a90>] iwl_rx_replenish_now+0x10/0x20 [iwlcore]
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<f853db37>] iwl_rx_handle+0x247/0x290 [iwlagn]
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c04988bb>] ? skb_dequeue+0x4b/0x70
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<f853dd3d>] iwl_irq_tasklet_legacy+0x1bd/0x3c0 [iwlagn]
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c0318e16>] ? rb_insert_color+0x76/0x100
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c014baa7>] tasklet_action+0xa7/0xc0
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c014cc40>] __do_softirq+0x90/0x1a0
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c019186c>] ? handle_IRQ_event+0x4c/0x140
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c0194514>] ? move_native_irq+0x14/0x50
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c014cd8d>] do_softirq+0x3d/0x40
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c014cecd>] irq_exit+0x5d/0x70
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c0104f10>] do_IRQ+0x50/0xc0
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c01711bc>] ? generic_smp_call_function_single_interrupt+0x7c/0x90
Dec  5 01:07:09 M1530 kernel: [40976.600004]  [<c01039b0>] common_interrupt+0x30/0x40
Dec  5 01:07:09 M1530 kernel: [40976.600004] Mem-Info:
Dec  5 01:07:09 M1530 kernel: [40976.600004] DMA per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.600004] CPU    0: hi:    0, btch:   1 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.600004] CPU    1: hi:    0, btch:   1 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.600004] Normal per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.600004] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.600004] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.600004] HighMem per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.600004] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.600004] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.600004] Active_anon:414590 active_file:90616 inactive_anon:92206
Dec  5 01:07:09 M1530 kernel: [40976.600004]  inactive_file:95990 unevictable:79220 dirty:2 writeback:25 unstable:0
Dec  5 01:07:09 M1530 kernel: [40976.600004]  free:108218 slab:12488 mapped:104190 pagetables:3108 bounce:0
Dec  5 01:07:09 M1530 kernel: [40976.600004] DMA free:3476kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:24kB inactive_file:16kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.600004] lowmem_reserve[]: 0 867 4042 4042
Dec  5 01:07:09 M1530 kernel: [40976.600004] Normal free:4208kB min:3732kB low:4664kB high:5596kB active_anon:45944kB inactive_anon:46024kB active_file:740kB inactive_file:436kB unevictable:316880kB present:887976kB pages_scanned:506 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.600004] lowmem_reserve[]: 0 0 25403 25403
Dec  5 01:07:09 M1530 kernel: [40976.600004] HighMem free:425188kB min:512kB low:3928kB high:7344kB active_anon:1612416kB inactive_anon:322800kB active_file:361700kB inactive_file:383508kB unevictable:0kB present:3251612kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.600004] lowmem_reserve[]: 0 0 0 0
Dec  5 01:07:09 M1530 kernel: [40976.600004] DMA: 3*4kB 5*8kB 2*16kB 4*32kB 1*64kB 3*128kB 3*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3476kB
Dec  5 01:07:09 M1530 kernel: [40976.600004] Normal: 842*4kB 61*8kB 0*16kB 1*32kB 0*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4144kB
Dec  5 01:07:09 M1530 kernel: [40976.600004] HighMem: 30609*4kB 17484*8kB 7606*16kB 1079*32kB 90*64kB 7*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 425188kB
Dec  5 01:07:09 M1530 kernel: [40976.600004] 215485 total pagecache pages
Dec  5 01:07:09 M1530 kernel: [40976.600004] 8627 pages in swap cache
Dec  5 01:07:09 M1530 kernel: [40976.600004] Swap cache stats: add 119944, delete 111317, find 4720/6252
Dec  5 01:07:09 M1530 kernel: [40976.600004] Free swap  = 7895004kB
Dec  5 01:07:09 M1530 kernel: [40976.600004] Total swap = 8000360kB
Dec  5 01:07:09 M1530 kernel: [40976.600004] 1179648 pages RAM
Dec  5 01:07:09 M1530 kernel: [40976.600004] 951810 pages HighMem
Dec  5 01:07:09 M1530 kernel: [40976.600004] 186328 pages reserved
Dec  5 01:07:09 M1530 kernel: [40976.600004] 489196 pages shared
Dec  5 01:07:09 M1530 kernel: [40976.600004] 502013 pages non-shared
Dec  5 01:07:09 M1530 kernel: [40976.621535] SLVoice: page allocation failure. order:2, mode:0x4020
Dec  5 01:07:09 M1530 kernel: [40976.621539] Pid: 16447, comm: SLVoice Tainted: P           2.6.31-15-generic-pae #50-Ubuntu
Dec  5 01:07:09 M1530 kernel: [40976.621541] Call Trace:
Dec  5 01:07:09 M1530 kernel: [40976.621547]  [<c05747ae>] ? printk+0x18/0x1a
Dec  5 01:07:09 M1530 kernel: [40976.621552]  [<c01ba2c0>] __alloc_pages_slowpath+0x340/0x480
Dec  5 01:07:09 M1530 kernel: [40976.621555]  [<c01ba50f>] __alloc_pages_nodemask+0x10f/0x120
Dec  5 01:07:09 M1530 kernel: [40976.621558]  [<c01ba567>] __get_free_pages+0x17/0x30
Dec  5 01:07:09 M1530 kernel: [40976.621562]  [<c01e3ed8>] __kmalloc_track_caller+0xd8/0x180
Dec  5 01:07:09 M1530 kernel: [40976.621566]  [<c049b2e3>] ? skb_copy+0x33/0x90
Dec  5 01:07:09 M1530 kernel: [40976.621569]  [<c04998ed>] __alloc_skb+0x4d/0x130
Dec  5 01:07:09 M1530 kernel: [40976.621572]  [<c049b2e3>] skb_copy+0x33/0x90
Dec  5 01:07:09 M1530 kernel: [40976.621578]  [<f83db4d8>] vboxNetFltLinuxPacketHandler+0x48/0xd0 [vboxnetflt]
Dec  5 01:07:09 M1530 kernel: [40976.621581]  [<c0128098>] ? default_spin_lock_flags+0x8/0x10
Dec  5 01:07:09 M1530 kernel: [40976.621585]  [<c04a406c>] netif_receive_skb+0x33c/0x580
Dec  5 01:07:09 M1530 kernel: [40976.621588]  [<c04988bb>] ? skb_dequeue+0x4b/0x70
Dec  5 01:07:09 M1530 kernel: [40976.621590]  [<c04a4317>] process_backlog+0x67/0xa0
Dec  5 01:07:09 M1530 kernel: [40976.621593]  [<c04a4a05>] net_rx_action+0xe5/0x1c0
Dec  5 01:07:09 M1530 kernel: [40976.621597]  [<c014cc40>] __do_softirq+0x90/0x1a0
Dec  5 01:07:09 M1530 kernel: [40976.621601]  [<c019186c>] ? handle_IRQ_event+0x4c/0x140
Dec  5 01:07:09 M1530 kernel: [40976.621603]  [<c0194514>] ? move_native_irq+0x14/0x50
Dec  5 01:07:09 M1530 kernel: [40976.621606]  [<c014cd8d>] do_softirq+0x3d/0x40
Dec  5 01:07:09 M1530 kernel: [40976.621609]  [<c014cecd>] irq_exit+0x5d/0x70
Dec  5 01:07:09 M1530 kernel: [40976.621612]  [<c0104f10>] do_IRQ+0x50/0xc0
Dec  5 01:07:09 M1530 kernel: [40976.621615]  [<c01711bc>] ? generic_smp_call_function_single_interrupt+0x7c/0x90
Dec  5 01:07:09 M1530 kernel: [40976.621618]  [<c01039b0>] common_interrupt+0x30/0x40
Dec  5 01:07:09 M1530 kernel: [40976.621620] Mem-Info:
Dec  5 01:07:09 M1530 kernel: [40976.621622] DMA per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.621624] CPU    0: hi:    0, btch:   1 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.621626] CPU    1: hi:    0, btch:   1 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.621627] Normal per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.621628] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.621630] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.621632] HighMem per-cpu:
Dec  5 01:07:09 M1530 kernel: [40976.621633] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.621635] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:07:09 M1530 kernel: [40976.621638] Active_anon:414590 active_file:90616 inactive_anon:92174
Dec  5 01:07:09 M1530 kernel: [40976.621639]  inactive_file:95990 unevictable:79270 dirty:2 writeback:25 unstable:0
Dec  5 01:07:09 M1530 kernel: [40976.621640]  free:108218 slab:12488 mapped:104190 pagetables:3108 bounce:0
Dec  5 01:07:09 M1530 kernel: [40976.621644] DMA free:3476kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:24kB inactive_file:16kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.621646] lowmem_reserve[]: 0 867 4042 4042
Dec  5 01:07:09 M1530 kernel: [40976.621652] Normal free:4208kB min:3732kB low:4664kB high:5596kB active_anon:45944kB inactive_anon:45896kB active_file:740kB inactive_file:436kB unevictable:317080kB present:887976kB pages_scanned:538 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.621654] lowmem_reserve[]: 0 0 25403 25403
Dec  5 01:07:09 M1530 kernel: [40976.621660] HighMem free:425188kB min:512kB low:3928kB high:7344kB active_anon:1612416kB inactive_anon:322800kB active_file:361700kB inactive_file:383508kB unevictable:0kB present:3251612kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:07:09 M1530 kernel: [40976.621662] lowmem_reserve[]: 0 0 0 0
Dec  5 01:07:09 M1530 kernel: [40976.621666] DMA: 3*4kB 5*8kB 2*16kB 4*32kB 1*64kB 3*128kB 3*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3476kB
Dec  5 01:07:09 M1530 kernel: [40976.621674] Normal: 842*4kB 61*8kB 0*16kB 1*32kB 0*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4144kB
Dec  5 01:07:09 M1530 kernel: [40976.621683] HighMem: 30609*4kB 17484*8kB 7606*16kB 1079*32kB 90*64kB 7*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 425188kB
Dec  5 01:07:09 M1530 kernel: [40976.621692] 215485 total pagecache pages
Dec  5 01:07:09 M1530 kernel: [40976.621693] 8627 pages in swap cache
Dec  5 01:07:09 M1530 kernel: [40976.621695] Swap cache stats: add 119976, delete 111349, find 4720/6252
Dec  5 01:07:09 M1530 kernel: [40976.621697] Free swap  = 7895004kB
Dec  5 01:07:09 M1530 kernel: [40976.621698] Total swap = 8000360kB
Dec  5 01:07:09 M1530 kernel: [40976.632869] 1179648 pages RAM
Dec  5 01:07:09 M1530 kernel: [40976.632872] 951810 pages HighMem
Dec  5 01:07:09 M1530 kernel: [40976.632874] 186328 pages reserved
Dec  5 01:07:09 M1530 kernel: [40976.632876] 489196 pages shared
Dec  5 01:07:09 M1530 kernel: [40976.632877] 502013 pages non-shared
Dec  5 01:07:09 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:08:43 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  5 01:15:02 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:16:23 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:29:28 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:30:42 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:30:47 M1530 pulseaudio[1928]: ratelimit.c: 7 events suppressed
Dec  5 01:32:19 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:35:19 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:37:04 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:39:46 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:41:33 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:42:04 M1530 pulseaudio[1928]: ratelimit.c: 2 events suppressed
Dec  5 01:42:09 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:42:33 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:44:30 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:47:21 M1530 kernel: [43389.403806] iwlagn invoked oom-killer: gfp_mask=0x40d0, order=2, oomkilladj=0
Dec  5 01:47:21 M1530 kernel: [43389.403811] iwlagn cpuset=/ mems_allowed=0
Dec  5 01:47:21 M1530 kernel: [43389.403815] Pid: 883, comm: iwlagn Tainted: P           2.6.31-15-generic-pae #50-Ubuntu
Dec  5 01:47:21 M1530 kernel: [43389.403817] Call Trace:
Dec  5 01:47:21 M1530 kernel: [43389.403826]  [<c01b79bf>] oom_kill_process+0x9f/0x250
Dec  5 01:47:21 M1530 kernel: [43389.403830]  [<c01b7fce>] ? select_bad_process+0xbe/0xf0
Dec  5 01:47:21 M1530 kernel: [43389.403833]  [<c01b8051>] __out_of_memory+0x51/0xa0
Dec  5 01:47:21 M1530 kernel: [43389.403836]  [<c01b80f3>] out_of_memory+0x53/0xb0
Dec  5 01:47:21 M1530 kernel: [43389.403839]  [<c01ba3ae>] __alloc_pages_slowpath+0x42e/0x480
Dec  5 01:47:21 M1530 kernel: [43389.403843]  [<c01ba50f>] __alloc_pages_nodemask+0x10f/0x120
Dec  5 01:47:21 M1530 kernel: [43389.403846]  [<c01ba567>] __get_free_pages+0x17/0x30
Dec  5 01:47:21 M1530 kernel: [43389.403851]  [<c01e3ed8>] __kmalloc_track_caller+0xd8/0x180
Dec  5 01:47:21 M1530 kernel: [43389.403856]  [<c04998cd>] ? __alloc_skb+0x2d/0x130
Dec  5 01:47:21 M1530 kernel: [43389.403875]  [<f837f843>] ? iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.403878]  [<c04998ed>] __alloc_skb+0x4d/0x130
Dec  5 01:47:21 M1530 kernel: [43389.403886]  [<f837f843>] iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.403895]  [<f8380ac3>] iwl_rx_replenish+0x23/0x50 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.403903]  [<f853cf80>] iwl_bg_rx_replenish+0x30/0x50 [iwlagn]
Dec  5 01:47:21 M1530 kernel: [43389.403908]  [<c015999e>] run_workqueue+0x6e/0x140
Dec  5 01:47:21 M1530 kernel: [43389.403914]  [<f853cf50>] ? iwl_bg_rx_replenish+0x0/0x50 [iwlagn]
Dec  5 01:47:21 M1530 kernel: [43389.403917]  [<c0159af8>] worker_thread+0x88/0xe0
Dec  5 01:47:21 M1530 kernel: [43389.403921]  [<c015e1a0>] ? autoremove_wake_function+0x0/0x40
Dec  5 01:47:21 M1530 kernel: [43389.403924]  [<c0159a70>] ? worker_thread+0x0/0xe0
Dec  5 01:47:21 M1530 kernel: [43389.403926]  [<c015deac>] kthread+0x7c/0x90
Dec  5 01:47:21 M1530 kernel: [43389.403929]  [<c015de30>] ? kthread+0x0/0x90
Dec  5 01:47:21 M1530 kernel: [43389.403933]  [<c0104007>] kernel_thread_helper+0x7/0x10
Dec  5 01:47:21 M1530 kernel: [43389.403935] Mem-Info:
Dec  5 01:47:21 M1530 kernel: [43389.403936] DMA per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.403938] CPU    0: hi:    0, btch:   1 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.403940] CPU    1: hi:    0, btch:   1 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.403941] Normal per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.403943] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.403945] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.403946] HighMem per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.403948] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.403949] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.403953] Active_anon:487508 active_file:95223 inactive_anon:98252
Dec  5 01:47:21 M1530 kernel: [43389.403954]  inactive_file:86188 unevictable:96209 dirty:0 writeback:62 unstable:0
Dec  5 01:47:21 M1530 kernel: [43389.403955]  free:11297 slab:12389 mapped:108840 pagetables:3667 bounce:0
Dec  5 01:47:21 M1530 kernel: [43389.403958] DMA free:3532kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.403961] lowmem_reserve[]: 0 867 4042 4042
Dec  5 01:47:21 M1530 kernel: [43389.403966] Normal free:6912kB min:3732kB low:4664kB high:5596kB active_anon:0kB inactive_anon:20kB active_file:76kB inactive_file:0kB unevictable:384836kB present:887976kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.403969] lowmem_reserve[]: 0 0 25403 25403
Dec  5 01:47:21 M1530 kernel: [43389.403974] HighMem free:34744kB min:512kB low:3928kB high:7344kB active_anon:1950032kB inactive_anon:392988kB active_file:380816kB inactive_file:344756kB unevictable:0kB present:3251612kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.403977] lowmem_reserve[]: 0 0 0 0
Dec  5 01:47:21 M1530 kernel: [43389.403981] DMA: 7*4kB 8*8kB 4*16kB 4*32kB 1*64kB 5*128kB 2*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3548kB
Dec  5 01:47:21 M1530 kernel: [43389.403990] Normal: 1330*4kB 3*8kB 8*16kB 3*32kB 3*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6912kB
Dec  5 01:47:21 M1530 kernel: [43389.403998] HighMem: 463*4kB 3210*8kB 395*16kB 20*32kB 2*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 34748kB
Dec  5 01:47:21 M1530 kernel: [43389.404007] 211523 total pagecache pages
Dec  5 01:47:21 M1530 kernel: [43389.404009] 10672 pages in swap cache
Dec  5 01:47:21 M1530 kernel: [43389.404011] Swap cache stats: add 147441, delete 136769, find 7009/9297
Dec  5 01:47:21 M1530 kernel: [43389.404012] Free swap  = 7876092kB
Dec  5 01:47:21 M1530 kernel: [43389.404014] Total swap = 8000360kB
Dec  5 01:47:21 M1530 kernel: [43389.416153] 1179648 pages RAM
Dec  5 01:47:21 M1530 kernel: [43389.416156] 951810 pages HighMem
Dec  5 01:47:21 M1530 kernel: [43389.416157] 186328 pages reserved
Dec  5 01:47:21 M1530 kernel: [43389.416159] 499146 pages shared
Dec  5 01:47:21 M1530 kernel: [43389.416160] 591802 pages non-shared
Dec  5 01:47:21 M1530 kernel: [43389.445379] iwlagn invoked oom-killer: gfp_mask=0x40d0, order=2, oomkilladj=0
Dec  5 01:47:21 M1530 kernel: [43389.445383] iwlagn cpuset=/ mems_allowed=0
Dec  5 01:47:21 M1530 kernel: [43389.445387] Pid: 883, comm: iwlagn Tainted: P           2.6.31-15-generic-pae #50-Ubuntu
Dec  5 01:47:21 M1530 kernel: [43389.445389] Call Trace:
Dec  5 01:47:21 M1530 kernel: [43389.445399]  [<c01b79bf>] oom_kill_process+0x9f/0x250
Dec  5 01:47:21 M1530 kernel: [43389.445402]  [<c01b7fce>] ? select_bad_process+0xbe/0xf0
Dec  5 01:47:21 M1530 kernel: [43389.445405]  [<c01b8051>] __out_of_memory+0x51/0xa0
Dec  5 01:47:21 M1530 kernel: [43389.445408]  [<c01b80f3>] out_of_memory+0x53/0xb0
Dec  5 01:47:21 M1530 kernel: [43389.445412]  [<c01ba3ae>] __alloc_pages_slowpath+0x42e/0x480
Dec  5 01:47:21 M1530 kernel: [43389.445415]  [<c01ba50f>] __alloc_pages_nodemask+0x10f/0x120
Dec  5 01:47:21 M1530 kernel: [43389.445418]  [<c01ba567>] __get_free_pages+0x17/0x30
Dec  5 01:47:21 M1530 kernel: [43389.445422]  [<c01e3ed8>] __kmalloc_track_caller+0xd8/0x180
Dec  5 01:47:21 M1530 kernel: [43389.445427]  [<c04998cd>] ? __alloc_skb+0x2d/0x130
Dec  5 01:47:21 M1530 kernel: [43389.445444]  [<f837f843>] ? iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.445447]  [<c04998ed>] __alloc_skb+0x4d/0x130
Dec  5 01:47:21 M1530 kernel: [43389.445455]  [<f837f843>] iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.445464]  [<f8380ac3>] iwl_rx_replenish+0x23/0x50 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.445472]  [<f853cf80>] iwl_bg_rx_replenish+0x30/0x50 [iwlagn]
Dec  5 01:47:21 M1530 kernel: [43389.445476]  [<c015999e>] run_workqueue+0x6e/0x140
Dec  5 01:47:21 M1530 kernel: [43389.445482]  [<f853cf50>] ? iwl_bg_rx_replenish+0x0/0x50 [iwlagn]
Dec  5 01:47:21 M1530 kernel: [43389.445485]  [<c0159af8>] worker_thread+0x88/0xe0
Dec  5 01:47:21 M1530 kernel: [43389.445489]  [<c015e1a0>] ? autoremove_wake_function+0x0/0x40
Dec  5 01:47:21 M1530 kernel: [43389.445492]  [<c0159a70>] ? worker_thread+0x0/0xe0
Dec  5 01:47:21 M1530 kernel: [43389.445495]  [<c015deac>] kthread+0x7c/0x90
Dec  5 01:47:21 M1530 kernel: [43389.445497]  [<c015de30>] ? kthread+0x0/0x90
Dec  5 01:47:21 M1530 kernel: [43389.445501]  [<c0104007>] kernel_thread_helper+0x7/0x10
Dec  5 01:47:21 M1530 kernel: [43389.445503] Mem-Info:
Dec  5 01:47:21 M1530 kernel: [43389.445505] DMA per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.445506] CPU    0: hi:    0, btch:   1 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.445508] CPU    1: hi:    0, btch:   1 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.445509] Normal per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.445511] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.445513] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.445514] HighMem per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.445516] CPU    0: hi:  186, btch:  31 usd: 173
Dec  5 01:47:21 M1530 kernel: [43389.445518] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.445521] Active_anon:465271 active_file:95203 inactive_anon:97512
Dec  5 01:47:21 M1530 kernel: [43389.445522]  inactive_file:86189 unevictable:96209 dirty:0 writeback:62 unstable:0
Dec  5 01:47:21 M1530 kernel: [43389.445523]  free:34143 slab:12389 mapped:103327 pagetables:3667 bounce:0
Dec  5 01:47:21 M1530 kernel: [43389.445527] DMA free:3532kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.445529] lowmem_reserve[]: 0 867 4042 4042
Dec  5 01:47:21 M1530 kernel: [43389.445534] Normal free:6908kB min:3732kB low:4664kB high:5596kB active_anon:0kB inactive_anon:20kB active_file:0kB inactive_file:0kB unevictable:384836kB present:887976kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.445537] lowmem_reserve[]: 0 0 25403 25403
Dec  5 01:47:21 M1530 kernel: [43389.445542] HighMem free:126380kB min:512kB low:3928kB high:7344kB active_anon:1860788kB inactive_anon:390028kB active_file:380816kB inactive_file:344756kB unevictable:0kB present:3251612kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.445545] lowmem_reserve[]: 0 0 0 0
Dec  5 01:47:21 M1530 kernel: [43389.445549] DMA: 7*4kB 8*8kB 4*16kB 4*32kB 1*64kB 5*128kB 2*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3548kB
Dec  5 01:47:21 M1530 kernel: [43389.445558] Normal: 1330*4kB 8*8kB 8*16kB 3*32kB 3*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6952kB
Dec  5 01:47:21 M1530 kernel: [43389.445566] HighMem: 10439*4kB 4793*8kB 2015*16kB 430*32kB 14*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 127124kB
Dec  5 01:47:21 M1530 kernel: [43389.445576] 211042 total pagecache pages
Dec  5 01:47:21 M1530 kernel: [43389.445578] 10186 pages in swap cache
Dec  5 01:47:21 M1530 kernel: [43389.445580] Swap cache stats: add 147441, delete 137255, find 7009/9297
Dec  5 01:47:21 M1530 kernel: [43389.445581] Free swap  = 7882712kB
Dec  5 01:47:21 M1530 kernel: [43389.445583] Total swap = 8000360kB
Dec  5 01:47:21 M1530 kernel: [43389.457754] 1179648 pages RAM
Dec  5 01:47:21 M1530 kernel: [43389.457756] 951810 pages HighMem
Dec  5 01:47:21 M1530 kernel: [43389.457758] 186328 pages reserved
Dec  5 01:47:21 M1530 kernel: [43389.457759] 493475 pages shared
Dec  5 01:47:21 M1530 kernel: [43389.457760] 562690 pages non-shared
Dec  5 01:47:21 M1530 kernel: [43389.469481] VirtualBox: page allocation failure. order:2, mode:0x44d0
Dec  5 01:47:21 M1530 kernel: [43389.469485] Pid: 9338, comm: VirtualBox Tainted: P           2.6.31-15-generic-pae #50-Ubuntu
Dec  5 01:47:21 M1530 kernel: [43389.469487] Call Trace:
Dec  5 01:47:21 M1530 kernel: [43389.469494]  [<c05747ae>] ? printk+0x18/0x1a
Dec  5 01:47:21 M1530 kernel: [43389.469500]  [<c01ba2c0>] __alloc_pages_slowpath+0x340/0x480
Dec  5 01:47:21 M1530 kernel: [43389.469503]  [<c01ba50f>] __alloc_pages_nodemask+0x10f/0x120
Dec  5 01:47:21 M1530 kernel: [43389.469506]  [<c01ba567>] __get_free_pages+0x17/0x30
Dec  5 01:47:21 M1530 kernel: [43389.469510]  [<c01e3ed8>] __kmalloc_track_caller+0xd8/0x180
Dec  5 01:47:21 M1530 kernel: [43389.469514]  [<c0167236>] ? getnstimeofday+0x56/0x110
Dec  5 01:47:21 M1530 kernel: [43389.469518]  [<c04998cd>] ? __alloc_skb+0x2d/0x130
Dec  5 01:47:21 M1530 kernel: [43389.469520]  [<c0495d6e>] ? sock_alloc_send_pskb+0x14e/0x270
Dec  5 01:47:21 M1530 kernel: [43389.469523]  [<c04998ed>] __alloc_skb+0x4d/0x130
Dec  5 01:47:21 M1530 kernel: [43389.469526]  [<c0495d6e>] sock_alloc_send_pskb+0x14e/0x270
Dec  5 01:47:21 M1530 kernel: [43389.469529]  [<c0495ea8>] sock_alloc_send_skb+0x18/0x20
Dec  5 01:47:21 M1530 kernel: [43389.469533]  [<c0513b66>] unix_stream_sendmsg+0x236/0x380
Dec  5 01:47:21 M1530 kernel: [43389.469537]  [<c0488014>] ? aa_cred_policy+0x14/0x30
Dec  5 01:47:21 M1530 kernel: [43389.469540]  [<c04949fb>] sock_aio_write+0x10b/0x120
Dec  5 01:47:21 M1530 kernel: [43389.469544]  [<c01ead35>] do_sync_readv_writev+0xb5/0xf0
Dec  5 01:47:21 M1530 kernel: [43389.469548]  [<c015e1a0>] ? autoremove_wake_function+0x0/0x40
Dec  5 01:47:21 M1530 kernel: [43389.469552]  [<c02cb85f>] ? security_file_permission+0xf/0x20
Dec  5 01:47:21 M1530 kernel: [43389.469554]  [<c01eafcf>] ? rw_verify_area+0x5f/0xe0
Dec  5 01:47:21 M1530 kernel: [43389.469557]  [<c01eb418>] ? rw_copy_check_uvector+0x78/0xf0
Dec  5 01:47:21 M1530 kernel: [43389.469560]  [<c01cc8b5>] ? do_anonymous_page+0x1e5/0x240
Dec  5 01:47:21 M1530 kernel: [43389.469563]  [<c01ebd7c>] do_readv_writev+0x9c/0x1c0
Dec  5 01:47:21 M1530 kernel: [43389.469566]  [<c04948f0>] ? sock_aio_write+0x0/0x120
Dec  5 01:47:21 M1530 kernel: [43389.469569]  [<c01ebee5>] vfs_writev+0x45/0x60
Dec  5 01:47:21 M1530 kernel: [43389.469572]  [<c01ebfed>] sys_writev+0x3d/0xa0
Dec  5 01:47:21 M1530 kernel: [43389.469575]  [<c0103283>] sysenter_do_call+0x12/0x28
Dec  5 01:47:21 M1530 kernel: [43389.469577] Mem-Info:
Dec  5 01:47:21 M1530 kernel: [43389.469578] DMA per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.469580] CPU    0: hi:    0, btch:   1 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.469582] CPU    1: hi:    0, btch:   1 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.469583] Normal per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.469585] CPU    0: hi:  186, btch:  31 usd:  61
Dec  5 01:47:21 M1530 kernel: [43389.469586] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.469588] HighMem per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.469589] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.469591] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.469594] Active_anon:444292 active_file:95203 inactive_anon:96402
Dec  5 01:47:21 M1530 kernel: [43389.469595]  inactive_file:86189 unevictable:96209 dirty:0 writeback:62 unstable:0
Dec  5 01:47:21 M1530 kernel: [43389.469596]  free:56318 slab:12389 mapped:103327 pagetables:3667 bounce:0
Dec  5 01:47:21 M1530 kernel: [43389.469599] DMA free:3524kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.469602] lowmem_reserve[]: 0 867 4042 4042
Dec  5 01:47:21 M1530 kernel: [43389.469607] Normal free:6756kB min:3732kB low:4664kB high:5596kB active_anon:0kB inactive_anon:20kB active_file:0kB inactive_file:0kB unevictable:384836kB present:887976kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.469610] lowmem_reserve[]: 0 0 25403 25403
Dec  5 01:47:21 M1530 kernel: [43389.469615] HighMem free:214992kB min:512kB low:3928kB high:7344kB active_anon:1777168kB inactive_anon:385588kB active_file:380816kB inactive_file:344756kB unevictable:0kB present:3251612kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:21 M1530 kernel: [43389.469618] lowmem_reserve[]: 0 0 0 0
Dec  5 01:47:21 M1530 kernel: [43389.469621] DMA: 7*4kB 7*8kB 3*16kB 4*32kB 1*64kB 5*128kB 2*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3524kB
Dec  5 01:47:21 M1530 kernel: [43389.469630] Normal: 1267*4kB 15*8kB 8*16kB 3*32kB 3*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 6756kB
Dec  5 01:47:21 M1530 kernel: [43389.469639] HighMem: 19902*4kB 8411*8kB 2928*16kB 580*32kB 40*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 214992kB
Dec  5 01:47:21 M1530 kernel: [43389.469648] 210635 total pagecache pages
Dec  5 01:47:21 M1530 kernel: [43389.469649] 9785 pages in swap cache
Dec  5 01:47:21 M1530 kernel: [43389.469651] Swap cache stats: add 147441, delete 137656, find 7010/9298
Dec  5 01:47:21 M1530 kernel: [43389.469653] Free swap  = 7886256kB
Dec  5 01:47:21 M1530 kernel: [43389.469654] Total swap = 8000360kB
Dec  5 01:47:21 M1530 kernel: [43389.480671] 1179648 pages RAM
Dec  5 01:47:21 M1530 kernel: [43389.480673] 951810 pages HighMem
Dec  5 01:47:21 M1530 kernel: [43389.480675] 186328 pages reserved
Dec  5 01:47:21 M1530 kernel: [43389.480677] 493434 pages shared
Dec  5 01:47:21 M1530 kernel: [43389.480678] 552487 pages non-shared
Dec  5 01:47:21 M1530 kernel: [43389.505371] iwlagn invoked oom-killer: gfp_mask=0x40d0, order=2, oomkilladj=0
Dec  5 01:47:21 M1530 kernel: [43389.505376] iwlagn cpuset=/ mems_allowed=0
Dec  5 01:47:21 M1530 kernel: [43389.505380] Pid: 883, comm: iwlagn Tainted: P           2.6.31-15-generic-pae #50-Ubuntu
Dec  5 01:47:21 M1530 kernel: [43389.505382] Call Trace:
Dec  5 01:47:21 M1530 kernel: [43389.505391]  [<c01b79bf>] oom_kill_process+0x9f/0x250
Dec  5 01:47:21 M1530 kernel: [43389.505394]  [<c01b7fce>] ? select_bad_process+0xbe/0xf0
Dec  5 01:47:21 M1530 kernel: [43389.505397]  [<c01b8051>] __out_of_memory+0x51/0xa0
Dec  5 01:47:21 M1530 kernel: [43389.505400]  [<c01b80f3>] out_of_memory+0x53/0xb0
Dec  5 01:47:21 M1530 kernel: [43389.505403]  [<c01ba3ae>] __alloc_pages_slowpath+0x42e/0x480
Dec  5 01:47:21 M1530 kernel: [43389.505407]  [<c01ba50f>] __alloc_pages_nodemask+0x10f/0x120
Dec  5 01:47:21 M1530 kernel: [43389.505410]  [<c01ba567>] __get_free_pages+0x17/0x30
Dec  5 01:47:21 M1530 kernel: [43389.505414]  [<c01e3ed8>] __kmalloc_track_caller+0xd8/0x180
Dec  5 01:47:21 M1530 kernel: [43389.505418]  [<c04998cd>] ? __alloc_skb+0x2d/0x130
Dec  5 01:47:21 M1530 kernel: [43389.505434]  [<f837f843>] ? iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.505437]  [<c04998ed>] __alloc_skb+0x4d/0x130
Dec  5 01:47:21 M1530 kernel: [43389.505445]  [<f837f843>] iwl_rx_allocate+0x73/0x1c0 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.505454]  [<f8380ac3>] iwl_rx_replenish+0x23/0x50 [iwlcore]
Dec  5 01:47:21 M1530 kernel: [43389.505461]  [<f853cf80>] iwl_bg_rx_replenish+0x30/0x50 [iwlagn]
Dec  5 01:47:21 M1530 kernel: [43389.505465]  [<c015999e>] run_workqueue+0x6e/0x140
Dec  5 01:47:21 M1530 kernel: [43389.505471]  [<f853cf50>] ? iwl_bg_rx_replenish+0x0/0x50 [iwlagn]
Dec  5 01:47:21 M1530 kernel: [43389.505474]  [<c0159af8>] worker_thread+0x88/0xe0
Dec  5 01:47:21 M1530 kernel: [43389.505478]  [<c015e1a0>] ? autoremove_wake_function+0x0/0x40
Dec  5 01:47:21 M1530 kernel: [43389.505481]  [<c0159a70>] ? worker_thread+0x0/0xe0
Dec  5 01:47:21 M1530 kernel: [43389.505483]  [<c015deac>] kthread+0x7c/0x90
Dec  5 01:47:21 M1530 kernel: [43389.505486]  [<c015de30>] ? kthread+0x0/0x90
Dec  5 01:47:21 M1530 kernel: [43389.505489]  [<c0104007>] kernel_thread_helper+0x7/0x10
Dec  5 01:47:21 M1530 kernel: [43389.505491] Mem-Info:
Dec  5 01:47:21 M1530 kernel: [43389.505493] DMA per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.505495] CPU    0: hi:    0, btch:   1 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.505496] CPU    1: hi:    0, btch:   1 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.505498] Normal per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.505499] CPU    0: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.505501] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:47:21 M1530 kernel: [43389.505503] HighMem per-cpu:
Dec  5 01:47:21 M1530 kernel: [43389.505504] CPU    0: hi:  186, btch:  31 usd: 163
Dec  5 01:47:22 M1530 kernel: [43389.505506] CPU    1: hi:  186, btch:  31 usd:   0
Dec  5 01:47:22 M1530 kernel: [43389.505509] Active_anon:419613 active_file:95203 inactive_anon:94737
Dec  5 01:47:22 M1530 kernel: [43389.505510]  inactive_file:86189 unevictable:96209 dirty:0 writeback:62 unstable:0
Dec  5 01:47:22 M1530 kernel: [43389.505511]  free:82620 slab:12389 mapped:103327 pagetables:3667 bounce:0
Dec  5 01:47:22 M1530 kernel: [43389.505514] DMA free:3524kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:22 M1530 kernel: [43389.505517] lowmem_reserve[]: 0 867 4042 4042
Dec  5 01:47:22 M1530 kernel: [43389.505522] Normal free:7148kB min:3732kB low:4664kB high:5596kB active_anon:0kB inactive_anon:20kB active_file:0kB inactive_file:0kB unevictable:384836kB present:887976kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:22 M1530 kernel: [43389.505525] lowmem_reserve[]: 0 0 25403 25403
Dec  5 01:47:22 M1530 kernel: [43389.505530] HighMem free:320304kB min:512kB low:3928kB high:7344kB active_anon:1677860kB inactive_anon:378928kB active_file:380816kB inactive_file:344756kB unevictable:0kB present:3251612kB pages_scanned:0 all_unreclaimable? no
Dec  5 01:47:22 M1530 kernel: [43389.505533] lowmem_reserve[]: 0 0 0 0
Dec  5 01:47:22 M1530 kernel: [43389.505536] DMA: 7*4kB 7*8kB 3*16kB 4*32kB 1*64kB 5*128kB 2*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3524kB
Dec  5 01:47:22 M1530 kernel: [43389.505545] Normal: 1329*4kB 34*8kB 10*16kB 3*32kB 3*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 7188kB
Dec  5 01:47:22 M1530 kernel: [43389.505554] HighMem: 31911*4kB 12090*8kB 3938*16kB 767*32kB 131*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 320428kB
Dec  5 01:47:22 M1530 kernel: [43389.505562] 210524 total pagecache pages
Dec  5 01:47:22 M1530 kernel: [43389.505564] 9678 pages in swap cache
Dec  5 01:47:22 M1530 kernel: [43389.505566] Swap cache stats: add 147441, delete 137763, find 7010/9298
Dec  5 01:47:22 M1530 kernel: [43389.505568] Free swap  = 7886988kB
Dec  5 01:47:22 M1530 kernel: [43389.505569] Total swap = 8000360kB
Dec  5 01:47:22 M1530 kernel: [43389.517539] 1179648 pages RAM
Dec  5 01:47:22 M1530 kernel: [43389.517541] 951810 pages HighMem
Dec  5 01:47:22 M1530 kernel: [43389.517543] 186328 pages reserved
Dec  5 01:47:22 M1530 kernel: [43389.517544] 460635 pages shared
Dec  5 01:47:22 M1530 kernel: [43389.517545] 558719 pages non-shared
Dec  5 01:47:42 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:47:59 M1530 pulseaudio[1928]: ratelimit.c: 4 events suppressed
Dec  5 01:48:31 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:49:29 M1530 pulseaudio[1928]: ratelimit.c: 1 events suppressed
Dec  5 01:49:41 M1530 pulseaudio[1928]: ratelimit.c: 10 events suppressed
```

P.S. Can anyone tell me what the ratelimit.c thing is that has flooded the log? Google led to nothing.

---

### Post by madverb on 2009-12-04
There are guides for removing pulseaudio to replace with ALSA or OSS4. I'm using OSS4. Sound quality definitely seems better. I'm unable to get 5.1 working with non 5.1 files though.

---

### Post by Ocxic on 2009-12-04
checkout: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Also pulse audio may not have correctly detected your audio buffer size, which is set by your audio chipset not how much memory you have in your system, so try plying with the "default-fragments" and "default-fragment-size-msec" values in "/etc/pulse/daemon.conf" (maybe lower them)they should be near the bottom of the file and then in a terminal or alt+f2 type "pulseaudio -k"(DO NOT RUN AS ROOT) to make the changes take effect.

default is usually 4-8 for the # of fragments and 10 for fragment size. different values may work better for you but it is all trial and error.

---

### Post by spongypants23 on 2009-12-05
Went ahead and removed PulseAudio, and I'm seeing improvements. System load doesn't go up to 10-12 when doing sound things anymore.

---

### Post by freedom on 2009-12-05
Any hint on how to remove Pulseaudio server from ubuntu?
Any link on some HOWTO? ;)

---

### Post by 0xABC123 on 2009-12-05
I used to have sound problems. I went to System->Administration->Sound and set everything to ALSA. Then I ran this command:
```

sudo apt-get remove pulseaudio

```All problems solved and system speed improved. :) It doesn't seem to be *that* integrated.

---

### Post by spongypants23 on 2009-12-06
> **0xABC123 said:**
> I used to have sound problems. I went to System->Administration->Sound and set everything to ALSA. Then I ran this command:
```

sudo apt-get remove pulseaudio

```All problems solved and system speed improved. :) It doesn't seem to be *that* integrated.

You must be using an older version of Ubuntu, then. Because in Karmic, the Sound menu chaned, and you can't select OSS/ALSA/ESD anymore.

---

### Post by NoaHall on 2009-12-06
You'll lose the little volume icon, but I have made a guide to remove it and set up keyboard shortcuts for turning up/down sound.

[http://usefulsoftwaregamesandknowledge.blogspot.com/2009/11/how-to-fix-sound-on-ubuntu-910karmic.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/11/how-to-fix-sound-on-ubuntu-910karmic.html)

---

### Post by 0xABC123 on 2009-12-06
> **spongypants23 said:**
> You must be using an older version of Ubuntu, then. Because in Karmic, the Sound menu chaned, and you can't select OSS/ALSA/ESD anymore.

Ubuntu 9.04. I forgot.:oops:

---

