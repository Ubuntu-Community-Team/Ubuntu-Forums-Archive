---
title: "can't record playing sound"
date: 2010-08-20
forum: General Help
---

### Post by kurci2 on 2010-08-20
Hi!
I want to record some sound witch i am playing on internet. I tried it with Audacity, but i can't record it. All i can record is sound form my MIC, but not what i'm playing through my speakers...

does anyone know what to do??

---

### Post by simosx on 2010-08-20
This should help you,
[http://www.youtube.com/watch?v=AwKyJRPlsxw](http://www.youtube.com/watch?v=AwKyJRPlsxw)

(it shows how to use PulseAudio to record audio from the sound card; it's the same info you get from lykeion)

---

### Post by lykeion on 2010-08-20
This is how I record audio from applications:

Nowadays Ubuntu uses PulseAudio, so to setup recording from 
an application you need PulseAudio Volume Control
> sudo apt-get install pavucontrol

[LIST=1]
[*]Start PulseAudio Volume Control (Applications > Sound & Video)

[*]Start the application plaing the sound (vlc, browser, or whatever)

[*]PulseAudio Volume Control > Playback Tab 
Make sure the application is listed there and that the level indicator registers the audio

[*]Start the capture, use Sound Recorder or Audacity

[*]PulseAudio Volume Control > Recording Tab 
Change Record stream from: "Internal Audio Analog Stero" to "Monitor of Internal Audio Analog Stereo"
[/LIST]

---

### Post by kurci2 on 2010-08-23
Thanks man!
Works perfectly!
I can mark this thread as solve now.

---

### Post by Thad E Ginathom on 2011-01-23
> **lykeion said:**
> 
[LIST=1]
[*]**Start the capture**, use Sound Recorder or Audacity
[*]PulseAudio Volume Control > Recording Tab 
Change Record stream from: "Internal Audio Analog Stero" to "Monitor of Internal Audio Analog Stereo"
[/LIST]


Having just been through this, for the second time, I found this thread.

Thought I'd **emphasise** that step two is not possible until step one has been done: there must be an application *actually recording* for its setting to appear on the Pulse Audio Volume Control tab. 

No recording application: recording tab is blank. That's what had me flummoxed, so it might confuse others too.

It may not be "intuitive" (quotes used to indicate what-ever-that-is!) but it is flexible, and works per application, so don't think (I did) that because you did it for *Sound Recorder*, it is done, eg. for *Audacity*. However, once set for the application, I think it is remembered.

If this sounds dumb, well... I am just beginning to understand the world of sound in Ubuntu, and there's just a chance that somebody else might be as dumb as I am ;)

---

