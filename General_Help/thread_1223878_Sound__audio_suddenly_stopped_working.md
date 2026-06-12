---
title: "Sound / audio suddenly stopped working"
date: 2009-07-26
forum: General Help
---

### Post by edmicman on 2009-07-26
I've had intermittent sound problems for awhile now; audio will work fine, but then usually after some flash video or something it wonks out.  Rebooting the computer has always fixed it until now.  Today I noticed that that the audio wasn't working when I was viewing a flash video.  I rebooted, and still nothing.  I tried playing an MP3, etc., and nothing comes out.  I know it was working as of a couple days ago, and I know that there were some updates installed recently, but I don't remember if they were before or after.  I do remember the last set of updates did include some pulseaudio things.

I'm on Ubuntu 9.04, upgraded sequentially since 8.04, on a Dell 600m Inspiron laptop.  Here's what lspci says:
```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
```

I don't immediately see anything in the messages or syslog.  Under System->Preferences->Sound, Playback options are all set to 'Autodetect'  Within those options I have listed the audio controller above with "ALSA" and "OSS", and then by themselves ALSA, ESD, OSS, and PulseAudio Sound Server.  I've tried switching the Sound Events and Music playback's to different options, and then testing...nothing ever happens.

I've done 'killall pulseaudio' and then 'pulseaudio -D' with the following:

```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
```

And also this:

```
peter@peter-laptop:~$ sudo alsa force-reload
[sudo] password for peter: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/peter/.gvfs
      Output information may be incomplete.
Terminating processes: 5325 9110lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/peter/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/peter/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/peter/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
peter@peter-laptop:~$ 
```

What else can I try, or how can I configure something or test something to find out what the heck is going on?

---

