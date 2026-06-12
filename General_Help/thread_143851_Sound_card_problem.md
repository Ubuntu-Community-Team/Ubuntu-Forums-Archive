---
title: "Sound card problem"
date: 2006-03-13
forum: General Help
---

### Post by dvm on 2006-03-13
Hi everyone, my computer at work has a VIA 8233 AC97 on-board sound card. lspci produces this:

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)

Though sound playback is fine I have yet to record with this card. What's more troubling is that in Applications->Sound & Video->Volume Control, it appears as I have 2 sound cards. The 8233 alsa mixer and an ICEnsemble ICE 1232 oss mixer.
When I click on the microphone selection box in the options tab GNOME locks up  and I need to reboot the pc from a tty (if I restart X, even though I login, GNOME doesn't come back up). Right now I need to write a program using the Java Sound API for audio recording and playback and I can't do any recording. I need to fix this fast but if I can't find a solution I might have to change back to dreaded windows. Please help

PS In alsamixer (from the shell) I get Card: VIA 8233, Chip: ICEnsemble 1232. So this sound card internally uses this chip?

---

