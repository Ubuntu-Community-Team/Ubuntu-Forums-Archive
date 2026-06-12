---
title: "Microphone hell"
date: 2006-05-04
forum: General Help
---

### Post by buttari on 2006-05-04
Hi,
I have Dapper installed on a Thinkpad t60p. Microphone is not working most of the times. Everything is unmuted either in alsamixer and gnome-volume-control (I don't know if there's a difference between the two). gnome-sound-recorder doesn't record anything, ekiga doesn't work, sjphone doesn't, skype doesn't. Sometimes if I start messing around with alsamixer/gnome-volume-control settings I can get it work but next time, the same settings, won't work. I had exactly the same problems with Breezy on a Thinkpad t40p.

Suggestions?

One more thing: in gnome-volume-control I have "microphone" and "front-mic"; can anybody explain me the difference between them?

Thanks

alfredo

---

### Post by louis_nichols on 2006-05-04
Your problem sounds very similar to a quite well known skype bug. So, in the particular case of skype, all that wouldn't be surprising at all.

As for the rest, just make sure everything uses alsa as input/output and unmute everything and you should be fine. Really. Alsamixer and gnome-volume-manager are just GUI's (actually one of them is a TUI) of the same thing. If you open them at the same time, you'll see that changing a setting in one will change the same setting in the other. If you got it to work once, it will work always, except for skype.

Google for skype_dsp_hijaker ! They say it helps, but I never could get it to work as they say. :( Maybe your luck with it will be better.

---

