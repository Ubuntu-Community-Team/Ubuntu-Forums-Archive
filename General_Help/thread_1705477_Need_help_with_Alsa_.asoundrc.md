---
title: "Need help with Alsa .asoundrc"
date: 2011-03-12
forum: General Help
---

### Post by landeel on 2011-03-12
Here's the deal, I have a net(note?)book (Sony Vaio VPC-YB15) that has 2 sound cards. One for internal speakers, mixer, headphones, etc. and another just for hdmi output.

This is what aplay -l tells me:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm using pure alsa here, no pulseaudio.

To make sound play from the internal speakers I need this .asoundrc file, or sound will not play at all:

```

pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}

```

I can get hdmi sound to play if I configure the sound output of programs to hw:0,3 HD-Audio Generic (this device has no mixer, only pcm).

But the problem is that some programs will just use Alsa defaults and won't let me configure the output.

Well, what I wanted to do is to play sound on both sound cards at the same time.

I know it's possible with .asoundrc : [http://alsa.opensrc.org/.asoundrc]("http://alsa.opensrc.org/.asoundrc")

But I couldn't figure it out. Every attempt to change my .asoundrc resulted in my machine mute again.

Please help!

---

