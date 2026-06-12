---
title: "Sound preferences doesn't launch"
date: 2011-01-11
forum: General Help
---

### Post by nagisa on 2011-01-11
I have installed Ubuntu 10.10 on my computer. The problem is that I can't run Sound Preferences window from here:[IMG]https://wiki.ubuntu.com/SoundMenu?action=AttachFile&do=get&target=cases.png[/IMG]
With that there's another problem:
Sound doesn't seem to be present in my Control Panel(neither it is in UbuntuMenu->Preferences:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180745&stc=1&d=1294754848[/IMG]

Why I noticed that you ask : Well, earlier I noticed that it doesn't move between 5.1 and Stereo when I plug in or out my headphones, so I had to change it manually every time. As I say, earlier it worked. Also sound is working perfectly, and I can control the volume. 

Oh by the way: Some logs
user.log
```

Jan  9 11:45:08 ubuntu pulseaudio[1481]: ratelimit.c: 45 events suppressed
Jan  9 11:58:27 ubuntu pulseaudio[1481]: ratelimit.c: 34 events suppressed
Jan  9 12:02:04 ubuntu pulseaudio[1481]: ratelimit.c: 208 events suppressed
Jan  9 12:03:12 ubuntu pulseaudio[1481]: ratelimit.c: 176 events suppressed
Jan  9 12:15:45 ubuntu pulseaudio[1481]: ratelimit.c: 45 events suppressed
Jan  9 12:38:53 ubuntu pulseaudio[1481]: ratelimit.c: 45 events suppressed
Jan  9 12:41:18 ubuntu pulseaudio[1481]: ratelimit.c: 210 events suppressed
Jan  9 12:43:59 ubuntu pulseaudio[1481]: ratelimit.c: 208 events suppressed
Jan  9 12:49:15 ubuntu pulseaudio[1481]: ratelimit.c: 39 events suppressed
Jan  9 13:00:51 ubuntu pulseaudio[1481]: ratelimit.c: 177 events suppressed
Jan  9 13:06:25 ubuntu pulseaudio[1481]: ratelimit.c: 41 events suppressed
Jan  9 13:13:48 ubuntu pulseaudio[1481]: ratelimit.c: 199 events suppressed
Jan  9 13:20:47 ubuntu pulseaudio[1481]: ratelimit.c: 198 events suppressed
Jan  9 13:26:41 ubuntu pulseaudio[1481]: ratelimit.c: 195 events suppressed
Jan  9 13:30:16 ubuntu pulseaudio[1481]: ratelimit.c: 197 events suppressed
Jan  9 13:30:46 ubuntu pulseaudio[1481]: ratelimit.c: 45 events suppressed
Jan  9 13:37:30 ubuntu pulseaudio[1481]: ratelimit.c: 41 events suppressed
Jan  9 14:11:25 ubuntu pulseaudio[1481]: ratelimit.c: 244 events suppressed
Jan  9 14:13:18 ubuntu pulseaudio[1481]: ratelimit.c: 203 events suppressed
Jan  9 14:18:52 ubuntu pulseaudio[1481]: ratelimit.c: 200 events suppressed
Jan  9 14:52:16 ubuntu pulseaudio[1481]: ratelimit.c: 192 events suppressed
Jan  9 15:18:06 ubuntu pulseaudio[1481]: ratelimit.c: 116 events suppressed
Jan  9 15:19:03 ubuntu pulseaudio[1481]: ratelimit.c: 198 events suppressed
Jan  9 15:32:15 ubuntu pulseaudio[1481]: ratelimit.c: 176 events suppressed
Jan  9 15:34:16 ubuntu pulseaudio[1481]: ratelimit.c: 202 events suppressed
Jan  9 17:29:25 ubuntu pulseaudio[1481]: ratelimit.c: 168 events suppressed
Jan  9 17:43:23 ubuntu pulseaudio[1481]: ratelimit.c: 178 events suppressed
Jan  9 17:46:45 ubuntu pulseaudio[1481]: ratelimit.c: 192 events suppressed
Jan  9 18:43:59 ubuntu pulseaudio[1481]: ratelimit.c: 185 events suppressed
Jan  9 18:47:05 ubuntu pulseaudio[1481]: ratelimit.c: 41 events suppressed
Jan  9 19:09:46 ubuntu pulseaudio[1481]: ratelimit.c: 207 events suppressed
Jan  9 19:22:29 ubuntu pulseaudio[1481]: ratelimit.c: 41 events suppressed
Jan  9 19:23:03 ubuntu pulseaudio[1481]: ratelimit.c: 227 events suppressed
Jan  9 19:23:11 ubuntu pulseaudio[1481]: ratelimit.c: 174 events suppressed
Jan  9 19:23:24 ubuntu pulseaudio[1481]: ratelimit.c: 196 events suppressed
Jan  9 19:23:36 ubuntu pulseaudio[1481]: ratelimit.c: 231 events suppressed
Jan  9 19:24:18 ubuntu pulseaudio[1481]: ratelimit.c: 215 events suppressed
Jan  9 19:24:34 ubuntu pulseaudio[1481]: ratelimit.c: 129 events suppressed
Jan  9 19:27:14 ubuntu pulseaudio[1481]: ratelimit.c: 235 events suppressed
Jan  9 19:29:35 ubuntu pulseaudio[1481]: ratelimit.c: 39 events suppressed
Jan  9 19:31:58 ubuntu pulseaudio[1481]: ratelimit.c: 1 events suppressed
Jan  9 19:32:59 ubuntu pulseaudio[1481]: ratelimit.c: 56 events suppressed
Jan  9 19:33:09 ubuntu pulseaudio[1481]: ratelimit.c: 66 events suppressed
Jan  9 19:41:12 ubuntu pulseaudio[1481]: ratelimit.c: 51 events suppressed
Jan  9 20:04:15 ubuntu pulseaudio[1481]: ratelimit.c: 41 events suppressed
Jan  9 20:28:15 ubuntu pulseaudio[1481]: ratelimit.c: 169 events suppressed
Jan  9 20:48:15 ubuntu pulseaudio[1481]: ratelimit.c: 109 events suppressed
Jan  9 20:52:24 ubuntu pulseaudio[1481]: ratelimit.c: 173 events suppressed
Jan  9 20:57:57 ubuntu pulseaudio[1481]: ratelimit.c: 215 events suppressed
Jan  9 21:19:07 ubuntu pulseaudio[1481]: ratelimit.c: 207 events suppressed
Jan  9 21:20:58 ubuntu pulseaudio[1481]: ratelimit.c: 164 events suppressed
Jan 10 15:46:45 ubuntu pulseaudio[1445]: ratelimit.c: 1 events suppressed
Jan 10 16:17:57 ubuntu pulseaudio[1445]: ratelimit.c: 41 events suppressed
Jan 10 16:18:12 ubuntu pulseaudio[1445]: ratelimit.c: 41 events suppressed
Jan 10 16:20:24 ubuntu pulseaudio[1445]: ratelimit.c: 41 events suppressed
Jan 10 17:19:43 ubuntu pulseaudio[1445]: ratelimit.c: 178 events suppressed
Jan 10 17:30:15 ubuntu pulseaudio[1445]: ratelimit.c: 192 events suppressed
Jan 10 17:31:40 ubuntu pulseaudio[1445]: ratelimit.c: 204 events suppressed
Jan 10 18:12:58 ubuntu pulseaudio[1445]: ratelimit.c: 145 events suppressed
Jan 10 19:09:58 ubuntu pulseaudio[1445]: ratelimit.c: 207 events suppressed
Jan 10 19:55:03 ubuntu pulseaudio[1445]: ratelimit.c: 173 events suppressed
Jan 10 20:25:22 ubuntu pulseaudio[1445]: ratelimit.c: 204 events suppressed
Jan 10 20:30:45 ubuntu pulseaudio[1445]: ratelimit.c: 43 events suppressed
Jan 10 20:39:33 ubuntu pulseaudio[1445]: ratelimit.c: 201 events suppressed
Jan 10 20:42:30 ubuntu pulseaudio[1445]: ratelimit.c: 37 events suppressed
Jan 10 20:52:38 ubuntu pulseaudio[1445]: ratelimit.c: 219 events suppressed
Jan 10 21:05:39 ubuntu pulseaudio[1445]: ratelimit.c: 197 events suppressed
Jan 10 21:18:34 ubuntu pulseaudio[1445]: ratelimit.c: 43 events suppressed
Jan 10 21:30:44 ubuntu pulseaudio[1445]: ratelimit.c: 44 events suppressed
Jan 10 21:44:53 ubuntu pulseaudio[1445]: ratelimit.c: 177 events suppressed
Jan 10 22:37:52 ubuntu pulseaudio[1445]: ratelimit.c: 199 events suppressed
Jan 10 23:08:28 ubuntu pulseaudio[1445]: ratelimit.c: 180 events suppressed
Jan 10 23:13:49 ubuntu pulseaudio[1445]: ratelimit.c: 44 events suppressed
Jan 10 23:22:44 ubuntu pulseaudio[1445]: ratelimit.c: 230 events suppressed
Jan 10 23:29:23 ubuntu pulseaudio[1445]: ratelimit.c: 47 events suppressed
Jan 11 15:38:07 ubuntu pulseaudio[1528]: ratelimit.c: 55 events suppressed
Jan 11 15:44:21 ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jan 11 16:10:24 ubuntu pulseaudio[1479]: ratelimit.c: 184 events suppressed
Jan 11 16:10:43 ubuntu pulseaudio[1479]: ratelimit.c: 194 events suppressed

```
I looked into what I did installed in that time:
GParted,
smplayer,
gnome-mplayer,
audacity,
wine,
furiousisomount,
inkscape,
GIMP,
And all dependencies to these.
Also I installed Visual C for Wine, maybe this have something to do with this?

---

### Post by nagisa on 2011-01-11
A small bump.

---

