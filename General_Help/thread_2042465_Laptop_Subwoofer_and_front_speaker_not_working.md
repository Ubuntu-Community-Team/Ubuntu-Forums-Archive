---
title: "Laptop Subwoofer and front speaker not working"
date: 2012-08-14
forum: General Help
---

### Post by BeastMode on 2012-08-14
I have an HP laptop with Beats Audio (g7) and decided to put Ubuntu on it just to see if finally, this time I would keep Ubuntu.

Things have been going swimmingly.  Linux was working better than ever, I was adjusting to Unity, I'd gotten everything I needed working to be working, except Netflix, iTunes, and gaming, which to me is an understood concept that Windows will just be necessary for.

Then, I started playing music.  In Windows, this laptop rocks with music.  Even for gaming, this laptop just does very well.  But, in Linux, the sound is limited to just two of the six speakers.

I have been off and on with Ununtu since 7.04, but I still don't know where to go to fix something like this, if at all.  For a laptop like this, having bad sound is unacceptable.  Can it be corrected?

---

### Post by BeastMode on 2012-08-14
I've performed searches on the issue, and I haven't really found anything to help with this, either, though I do see a couple of discussions on it.  

Is it just one of those unsolveable problems?  If so, why?  Is it just that the technology for this kind of sound out of a laptop is relatively new, or not enough of them have something like this, so it's not really accounted for in the development?

---

### Post by BeastMode on 2012-08-17
Shameless bump, please.

I really would appreciate some help.

---

### Post by Zvlwab on 2012-08-17
You probably need to edit the /etc/pulse/daemon.conf file.
I use a 5.1 surround set and this works for me:
```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = yes

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0
```

I believe the key lines are
```

default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
```

---

### Post by ketchup94 on 2013-04-28
I found many threads, Hopefully this works for you. I copied this from another website's forum 
[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/quot-Beats-Audio-quot-Linux-HP-Envy-17/td-p/520175](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/quot-Beats-Audio-quot-Linux-HP-Envy-17/td-p/520175)

additional thread
[COLOR=#000000][FONT=HPRegular][http://ubuntuforums.org/showthread.php?t=1605735&page=3](http://ubuntuforums.org/showthread.php?t=1605735&page=3)[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Just add this line[/FONT][/COLOR]

options snd-hda-intel model=ref[COLOR=#000000][FONT=HPRegular] In this file :[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular] [/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular] [/FONT][/COLOR]

/etc/modprobe.d/alsa-base.conf[COLOR=#000000][FONT=HPRegular] (sudo gedit /etc/modprobe.d/alsa-base.conf)[/FONT][/COLOR]

---

