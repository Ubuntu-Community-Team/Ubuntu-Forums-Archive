---
title: "Possible Hard-Drive related performance problem?"
date: 2010-02-14
forum: General Help
---

### Post by finalhit on 2010-02-14
This is a bit frustrating, I don't seem to experience this on my windows partition in this machine, so I'm not quite sure what's going on.

Ubuntu seems to just have a horrible horrible performance problem in my machine (only have a single machine with Ubuntu, so I can't compare)

On this laptop, all I basically do is surf the web (youtube, flash), download stuff, and watch movies. Seems like something 1.6 Ghz Turion x2 / 512 Mb should be able to handle without problem, but depending on some unknown combination of parameters, I just get horrible horrible performance (my machine just hangs a lot, to the point that mouse doesn't respond)

I seem to see a correlation to the hard drive activity. Everytime I'm downloading, performance just drags...perhaps it's something to do with swaps?

In windows, whenever an application hangs, I still have access to the rest of the OS (start menu, task manager, etc). But when Ubuntu hangs, it seems the OS itself hangs.

My CPU stays relatively normal, and the performance hit only occurs whenever my hard-drive is somewhat busy. 

Also, there seems to be not a consistent problem (although a frequent one) so it affirms my suspicion that this is not a hardware problem (maybe?).

I also use JDownloader to download stuff, which is a Java app. Unequivocally, whenever I run this app, the system just bogs down. It runs perfectly well under windows. Whenever I minimize it, and then restore, it seems to take an abnormal amount of time before the UI becomes accessible (it draws the last state, pre-minimize, and takes forever to draw it's current state)


Can anyone point me to a direction to possibly fix this? I really want to keep Ubuntu, but this seems to be an intolerable problem.

---

### Post by ironclaw on 2010-02-14
Try running
```
dmesg | tail
```
when you get a performance hit to see if there any messages from the kernel.

Or examine /var/log/messages for more output.

---

### Post by finalhit on 2010-02-17
its seems like my problem stems from the same pulseaudio problem many have having the same issues with. My logs are filled with:

pulseaudio[1826]: ratelimit.c: 8 events suppressed

I think this maybe the same source from my startup problem, that after the login, sometimes, my machine just hangs and needs a hard reboot. 

it doesn't happen all the time, but it's really bothersome. The thread regarding the issue doesn't seem to have any solutions.

---

### Post by tgalati4 on 2010-02-17
sudo apt-get install htop
htop

Take note of  processes eating up CPU cycles.

---

### Post by finalhit on 2010-02-17
yup, everytime i get a hickup, /usr/binpulseaudio --start is at the top of the list (sorted by CPU%)

anyone have any recommendations/fix/workarounds? I've been doing my research, but there doesn't seem to be a clean way to remove/replace pulseaudio

---

### Post by tgalati4 on 2010-02-17
What is the exact error you are getting in your logs?  If 8 similar messages are suppressed, what was the first one?  Sounds like a pulseaudio configuration problem--as opposed to a hard disk problem.

What is the output of:

pulseaudio --dump-conf

To learn more about pulseaudio:

man pulseaudio

---

### Post by finalhit on 2010-02-19
pulseaudio- --dump-conf
> daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
cpu-limit = no
enable-shm = yes
flat-volumes = no
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-0.9.19/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = auto
log-level = notice
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 2
default-channel-map = front-left,front-right
default-fragments = 8
default-fragment-size-msec = 10
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 1000000



with regards to the error being suppressed, I don't think messages are being suppressed. I think the error itself is "pulseaudio[1826]: ratelimit.c: 8 events suppressed", where 8 can be any integer ranging from 1 to 100+ from what i've seen.

That is the error itself, it's not a suppression of similar errors.

---

### Post by dcstar on 2010-02-19
> **finalhit said:**
> 
.........
In windows, whenever an application hangs, I still have access to the rest of the OS (start menu, task manager, etc). But when Ubuntu hangs, it seems the OS itself hangs.

My CPU stays relatively normal, and the performance hit only occurs whenever my hard-drive is somewhat busy. 

Also, there seems to be not a consistent problem (although a frequent one) so it affirms my suspicion that this is not a hardware problem (maybe?).
.........

Run a full SMART test on your disk for bad blocks.

---

### Post by finalhit on 2010-02-20
smart test results

> # 1  Extended offline    Completed without error       00%     11871         -

---

