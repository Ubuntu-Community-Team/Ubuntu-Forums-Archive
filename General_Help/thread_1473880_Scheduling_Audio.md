---
title: "Scheduling Audio"
date: 2010-05-05
forum: General Help
---

### Post by dclarion on 2010-05-05
I am wondering about scheduling audio playback under Ubuntu.  The background is this:  My birthday is fast approaching, and I always try to do something to remember the best birthday gift I ever received, that being the Apollo 11 mission; Neil and Buzz landed on my 12th birthday.

Anyway, I have a wagonload of audio from nasa.gov and would like to schedule the MP3s to play in real time.  'at' won't do it, at least with 'mplayer'; I've tried.  I suspect that because there is no controlling terminal for jobs run under 'at', the audio has no place to go.  Is there some way to get a controlling terminal for these audio playback jobs, or specify a destination to some player?

Many much thanks in advance.

---

### Post by StuartN on 2010-05-05
> **dclarion said:**
> 'at' won't do it, at least with 'mplayer'; I've tried.  I suspect that because there is no controlling terminal for jobs run under 'at', the audio has no place to go.

I use mplayer with cron for alarms, so it should work with at. My cron job says **mplayer ~/alarm-clock-sound.mp3**, but it might be wise to use absolute paths.

---

