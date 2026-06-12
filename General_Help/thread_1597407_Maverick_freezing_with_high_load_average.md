---
title: "Maverick freezing with high load average"
date: 2010-10-15
forum: General Help
---

### Post by sir.hampster on 2010-10-15
Hello,

it's the fourth time now since Maverick that I had to cold reboot my system because it was totally unresponsive.

The system monitor in my taskbar shows 100% on the background blue graph (I guess that's just one core then) and almost nothing on the other core.
On the last freeze I managed to open 'sudo top' before it went totally unresponsive and saw that there was no high CPU usage at all, but a load average spiking above 24.
Also the swap seemed to be full although my machine usually never uses swap.

I was watching a movie with VLC this time, but I'm not sure if VLC ran the other times my OS froze.

I made a snapshot with my cell phone: [http://correnz.net/upload/freeze.JPG](http://correnz.net/upload/freeze.JPG)

Can anybody tell me how I can prevent a process from causing so much load?

Best wishes

---

### Post by matt_symes on 2010-10-15
Hi,

Have you checked the logs? They should give a clue to this issue. Definitely not a hardware problem?

Your not the first person to have this issue, so a search on these forums might prove productive.

Kind regards

---

### Post by matt_symes on 2010-10-15
Hi,

To limit a process you can use CPU limit

here is a tutorial

[http://maketecheasier.com/limit-cpu-usage-of-any-process-in-linux/2010/09/22](http://maketecheasier.com/limit-cpu-usage-of-any-process-in-linux/2010/09/22)

Kind regards

---

### Post by spoon_ on 2010-10-15
I'm not sure from your post whether you saw this or not, but VLC is consuming a huge amount of your memory for some reason. The high CPU load is really io wait load -- the system trying to use swap as memory. So the question is why is VLC eating so much memory?

---

### Post by matt_symes on 2010-10-15
Hi,

well spotted spoon_. good call. 

OP. Your not transcoding on the fly or something are you? Frame buffers have to be stored somewhere for transcoding. What type of file was it. Can you test it on another machine

Kind regards

---

### Post by matt_symes on 2010-10-15
Hi,

This is interesting...

[http://trac.videolan.org/vlc/ticket/4145](http://trac.videolan.org/vlc/ticket/4145)

If it happens again keep a note of the applications running.

Kind regards.

---

### Post by sir.hampster on 2010-10-15
sorry, I am no expert here, I am not familiar with logs and what's normal there and what is a worthy piece of information.

I saw through the /var/log/systlog of the time of the freeze and saw a lot of stuff I do not understand. But among it there were many processes the system killed due to lack of memory.. like this:

> Oct 15 14:18:30 einstein kernel: [45143.853311] Out of memory: kill process 16397 (knotify4) score 112569 or a child
Oct 15 14:18:30 einstein kernel: [45143.853315] Killed process 16397 (knotify4) vsz:900552kB, anon-rss:0kB, file-rss:48kBHowever there are a lot of those:
> Oct 15 13:45:18 einstein pulseaudio[2175]: ratelimit.c: 1735 events suppressedall the time apparently while I was watching the movie

And later there is this bug-report (four times actually, 14:12, 14:19, 14:22, 14:27), if I can call it this way:

> Oct 15 14:19:03 einstein pulseaudio[2175]: ratelimit.c: 118 events suppressed
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: -1842824 bytes (-10446 ms).
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: snd_pcm_dump():
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: Soft volume PCM
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: Control: PCM Playback Volume
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: min_dB: -51
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: max_dB: 0
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: resolution: 256
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c: Its setup is:
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   stream       : PLAYBACK
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   access       : MMAP_INTERLEAVED
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   format       : S16_LE
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   subformat    : STD
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   channels     : 2
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   rate         : 44100
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   exact rate   : 44100 (44100/1)
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   msbits       : 16
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   buffer_size  : 88192
Oct 15 14:19:03 einstein pulseaudio[2175]: alsa-util.c:   period_size  : 44096
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   period_time  : 999909
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   tstamp_mode  : ENABLE
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   period_step  : 1
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   avail_min    : 61028
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   period_event : 0
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   start_threshold  : -1
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   stop_threshold   : 6205960286516543488
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   silence_threshold: 0
Oct 15 14:19:04 einstein pulseaudio[2175]: alsa-util.c:   silence_size : 0
Oct 15 14:19:05 einstein pulseaudio[2175]: alsa-util.c:   boundary     : 6205960286516543488
Oct 15 14:19:05 einstein pulseaudio[2175]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Oct 15 14:19:05 einstein pulseaudio[2175]: alsa-util.c: Its setup is:
Oct 15 14:19:05 einstein pulseaudio[2175]: alsa-util.c:   stream       : PLAYBACK
But I cannot tell if this pulseaudio thing is the cause or another symptom of the freeze.

---

