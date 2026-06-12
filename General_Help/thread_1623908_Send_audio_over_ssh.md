---
title: "Send audio over ssh?"
date: 2010-11-17
forum: General Help
---

### Post by t0p on 2010-11-17
I have a puny netbook (deimos) and a more powerful desktop machine (phobos).  Sometimes I want to watch a video file on deimos; but it's so puny, the video won't play properly, lagging behind the audio or skipping frames.

A solution I have hit on is to use ssh -X, to use phobos's more powerful guts to send the video over to deimos.  This works, except for one annoying problem: the video is coming over just fine, but the audio is played on phobos's loudspeakers, not on deimos's speakers.

How do I rectify this problem?

---

### Post by KeyserSoze93 on 2010-11-17
Consider using pulseaudio. While I've never seen the draw of it for one-machine desktop audio, pulse is great for what it was designed for: network audio streaming.

Install the padevchooser package on the laptop. Start it from the terminal or the applications menu - you will get a little icon in your system tray.

Left-click it, select "Configure Local Sound Server", then go to the Network Server tab and tick "Enable Network Access To Local Sound Devices" and "Do Not Require Authentication".

On your desktop PC, run (in the same terminal, on after the other):

```

export PULSE_SERVER=<ip of your laptop>

<your media player>

```

You'll need to set up your media player for pulseaudio output but that should be fairly simple.

For mplayer, I just run:

```

export PULSE_SERVER=192.168.0.4

mplayer -ao pulse blah.mov

```

If all goes well, you should get sound coming from your laptop and, if you launched it from an X-forwarded session, video on your laptop too.

---

### Post by t0p on 2010-11-24
Thanks KeyserSozer93, that worked just fine.

---

