---
title: "Pulseaudio + Flash problem (no audio + video gets stuck buffering)"
date: 2012-06-27
forum: General Help
---

### Post by aoen on 2012-06-27
Symptoms:
[LIST]
After I spend some time logged in on my computer, flash videos will play without sound, and after about 7 seconds of playback the video will get stuck buffering until I click somewhere on the seek bar.
[/LIST]
[LIST]
No audio devices show in the gnome control panel
[/LIST]

Testing:
[LIST]
HTML5 audio works fine.
[/LIST]
[LIST]
The problem exists in both chromium and flash.
[/LIST]
[LIST]
Non-flash sounds play fine
[/LIST]

Attempted Fixes:
[LIST]
Restarting pulseaudio (doesn't work)
[/LIST]
[LIST]
Purging pulseaudio and alsa packages and reinstalling
[/LIST]

Deleting ~/.pulse and ~/.pulse-cookie and restarting my browser fixes the problem temporarily.

---

