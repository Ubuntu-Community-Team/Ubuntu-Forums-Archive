---
title: "Watching Youtube causes system freeze/ X crash"
date: 2011-08-30
forum: General Help
---

### Post by LADmaticCA on 2011-08-30
I can no longer watch youtube videos on my Ubuntu 10.10 64bit install...well I can watch maybe a couple then my X session will freeze, requiring a manual power down. 

I have tried using different browsers and the results are the same. I tried using other kernels, still the same result. I am using the newest adobe labs flash 11 beta 2 64bit. I have Arch and openSUSE 11.4 on this same machine using the same flash plugin with no problems at all. 

Any help would be appreciated. Below is the system output from the time of my most recent crash/freeze:

```
Aug 30 07:30:37 maverickBox pulseaudio[2011]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Aug 30 07:30:37 maverickBox pulseaudio[2011]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
Aug 30 07:30:37 maverickBox pulseaudio[2011]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Aug 30 07:31:01 maverickBox pulseaudio[2011]: ratelimit.c: 17 events suppressed
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 411244 bytes (2331 ms).
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c: snd_pcm_dump():
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c: Hooks PCM
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c: Its setup is:
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   stream       : PLAYBACK
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   access       : MMAP_INTERLEAVED
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   format       : S16_LE
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   subformat    : STD
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   channels     : 2
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   rate         : 44100
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   exact rate   : 44100 (44100/1)
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   msbits       : 16
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   buffer_size  : 16384
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   period_size  : 16384
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   period_time  : 371519
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   tstamp_mode  : ENABLE
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   period_step  : 1
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   avail_min    : 16384
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   period_event : 0
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   start_threshold  : -1
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   stop_threshold   : 4611686018427387904
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   silence_threshold: 0
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   silence_size : 0
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   boundary     : 4611686018427387904
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c: Slave: Hardware PCM card 1 'SB Live! 5.1 [SB0220]' device 0 subdevice 0
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c: Its setup is:
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   stream       : PLAYBACK
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   access       : MMAP_INTERLEAVED
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   format       : S16_LE
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   subformat    : STD
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   channels     : 2
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   rate         : 44100
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   exact rate   : 44100 (44100/1)
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   msbits       : 16
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   buffer_size  : 16384
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   period_size  : 16384
Aug 30 07:31:04 maverickBox pulseaudio[2011]: alsa-util.c:   period_time  : 371519
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   tstamp_mode  : ENABLE
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   period_step  : 1
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   avail_min    : 16384
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   period_event : 0
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   start_threshold  : -1
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   stop_threshold   : 4611686018427387904
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   silence_threshold: 0
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   silence_size : 0
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   boundary     : 4611686018427387904
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   appl_ptr     : 29858740
Aug 30 07:31:05 maverickBox pulseaudio[2011]: alsa-util.c:   hw_ptr       : 29945167
Aug 30 07:35:02 maverickBox kernel: imklog 4.2.0, log source = /proc/kmsg started.
```

*edit
Okay, I'm getting similar crashes with Vimeo. With firefox I get a full system freeze. With Chromium I get a "Oops, something broke" message. I tried using the html5 player in Vimeo and it still crashes.

---

### Post by dodo3773 on 2011-08-31
Not sure if this helps but I have had problems in the past with videos freezing and found that most of them were related to compositing. Do you run compiz or something similar? Do you get the same problems in metacity (assuming you are using gnome).

---

### Post by LADmaticCA on 2011-08-31
I am running Gnome with compiz. I will try with metacity and see what happens.

---

### Post by dodo3773 on 2011-08-31
> **LADmaticCA said:**
> I am running Gnome with compiz. I will try with metacity and see what happens.

If that is the problem there is always the solution of switching to watch videos / play games. I did that for a long time. I prefer to just run 2 X sessions though so I can switch with ctrl+alt+F7-8 (one gnome3 fallback+compiz the other openbox).

---

### Post by LADmaticCA on 2011-09-04
Well I tried using Metacity and the results are still the same. I'm guessing either something got broken with an update or I have over tweaked something.

---

### Post by dodo3773 on 2011-09-04
> **LADmaticCA said:**
> Well I tried using Metacity and the results are still the same. I'm guessing either something got broken with an update or I have over tweaked something.

Are you running a 32 bit flash in a 64 bit distro? Also, have you tried tweaking some of the flash options (mms.cfg)? Other than that I don't know.

---

### Post by LADmaticCA on 2011-09-04
I'm using the 64bit flash from adobe labs. I am not familiar with the flash options you speak of...mms.cfg?

Thanks for your suggestions by the way. I'm not sure what else to try myself other than a re-install.

---

### Post by dodo3773 on 2011-09-04
> **LADmaticCA said:**
> I'm using the 64bit flash from adobe labs. I am not familiar with the flash options you speak of...mms.cfg?

Thanks for your suggestions by the way. I'm not sure what else to try myself other than a re-install.

Read the Arch wiki entry on flash. All of those options should work on Ubuntu as well.

---

