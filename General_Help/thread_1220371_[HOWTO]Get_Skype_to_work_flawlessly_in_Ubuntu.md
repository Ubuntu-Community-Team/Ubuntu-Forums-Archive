---
title: "[HOWTO]Get Skype to work flawlessly in Ubuntu"
date: 2009-07-22
forum: General Help
---

### Post by kn100 on 2009-07-22
Ok, so you may have noticed that skype does NOT like sharing its audio with other audio using apps, so when you use Skype, you cant listen to music, and vice versa. Here is a quick and easy fix.
First off, Click system, preferences , sound. Then set the top four drop down boxes to Alsa.

Next, open Skype, click the little Skype logo in the bottom left of the Skype contacts window, then click options, Then click Sound Devices. In here, set the top one to your microphone, and the bottom two to PulseAudio.
There you have it, now Ubuntu and Skype can live in harmony!

This works because now every noise Ubuntu makes goes through Alsa, while skype goes through PulseAudio, meaning Skype can take up the relatively useless Pulseaudio and live there, and Ubuntu can use Alsa

Hope this helps someone!
Kevin

---

