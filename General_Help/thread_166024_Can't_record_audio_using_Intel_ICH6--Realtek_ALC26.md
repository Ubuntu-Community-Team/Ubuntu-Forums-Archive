---
title: "Can't record audio using Intel ICH6--Realtek ALC260"
date: 2006-04-25
forum: General Help
---

### Post by stepasha on 2006-04-25
I am trying to get my microphone working under Dapper Beta. I was able to record fine when I first installed Dapper flight CD 4, but after an update I have never been able to get recording working again. I am now using Dapper 6.06 Beta. I don't know what changed between then and now. Clearly this card can work, but I don't know where the problem lies.

I can play sounds fine. I can even play sounds from multiple apps at the same time, but I can't record. I've tried killing esd (a suggestion from ubuntu forums), and I've unmuted everything. I can hear myself through the microphone when I unmute it, which would suggest a permissions problem, but I have write permissions to /dev/dsp as part of the audio group.

Sound Recorder acts like it records, but when you play it back, it's just silence. Audacity won't even let me choose a device to record from.

I've been googling for fixes to this all week, but can't seem to find any. I would be happy to submit a bug report, but I don't know which app to say it's in reference to. Alsa? Gstreamer?


I am using:

Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

$ tail -2 /proc/asound/oss/sndstat--gives me:

Mixers:
0: Realtek ALC260

I hope someone out there knows the answer to this one.

---

### Post by daka on 2007-01-19
did you end up solving the problem?

I have same problem

---

