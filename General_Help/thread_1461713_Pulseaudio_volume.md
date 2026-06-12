---
title: "Pulseaudio volume"
date: 2010-04-24
forum: General Help
---

### Post by Firestorm21 on 2010-04-24
I'm having issues controlling the volume. I'm using a Dell E1705.

The audio card has 3 channels: Master, PCM, and LFE. When I use the keyboard volume controls, pulse maxes out PCM and LFE, then slowly raises the Master channel.

The LFE channel controls the mini-subwoofer in the bottom of the laptop. When pulse maxes out the volume, the sub is really loud while the other speakers are quiet since Master isn't up high enough yet.

Is there a way to have Pulse control both the Master and LFE channels and have pulse leave PCM alone?

---

### Post by Firestorm21 on 2010-04-25
If I manually change the sound in alsamixer to like 40, 80, 40 (Master, PCM, LFE), then Pulse will randomly just change it back to whatever it feels like. Right now it changed it back to 6, 99, 100 (Master, PCM, LFE).

Any ideas? I'd like to run Ubuntu because it seems to be easier to maintain than what I was running, but I'm not going to risk destroying the speakers in my laptop just to stay with it.

---

### Post by Firestorm21 on 2010-04-27
Bump..............

---

### Post by lidex on 2010-04-27
This may help:
> There are a few variables which control how PulseAudio controls the volume. You can either edit /etc/pulse/default.pa (you'll have to be root to do that) to change the behavior for all users, or copy that file to ~/.pulse/default.pa and then edit that file, to change behavior for the current user only.

Open the file mentioned above. Find the row saying "load-module module-udev-detect" and change it to:

load-module module-udev-detect ignore_dB=1

To try your changes, restart PulseAudio with the following command:

killall pulseaudio

PulseAudio will then autospawn (restart itself).

You may find that the above workaround is insufficient, in which case you may configure PulseAudio to control only one mixer control, e.g., PCM (cf. alsamixer). Find the row saying "#load-module module-alsa-sink" and change it to:

load-module module-alsa-sink control=PCM

(remember to remove the # in the beginning of the row!) Optionally replace PCM with the mixer control you want PulseAudio to control.

You will then need to killall pulseaudio as above and allow the daemon to autospawn. 

---

