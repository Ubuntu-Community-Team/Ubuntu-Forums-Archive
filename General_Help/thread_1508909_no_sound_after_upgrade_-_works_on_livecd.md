---
title: "no sound after upgrade - works on livecd"
date: 2010-06-13
forum: General Help
---

### Post by jamesorr on 2010-06-13
I upgraded my desktop from 9.10 to 10.04 and I have no sound.

When I boot from the 10.04 livecd, sound works fine.

gnome-volume-control does not get loaded into the taskbar, when I run it from the console there is nothing listed under hardware.

I also tried creating a fresh new user account, no sound on that either but gnome-volume-control does get loaded into taskbar but still nothing under hardware.

aplay -l does list sound devices ...

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```alsamixer shows the card and mixer levels, but aplay somemusic.mp3 does not result in any sound (no error, it looks like it's playing but no sound).

lspci -v shows ...
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7528
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```As it works fine on the livecd, how I can I reset my sound config so that it's the same as what the livecd uses?

---

### Post by jamesorr on 2010-06-14
If the sound works on the LiveCD there must be something I can do to get it working on the installation??  Anybody?

---

### Post by jamesorr on 2010-06-15
Still an issue ...

---

### Post by cbrunhaver on 2010-06-15
Not en expert in this but you might try typing this in the terminal:

pulseaudio -k

---

### Post by jamesorr on 2010-06-15
> **cbrunhaver said:**
> Not en expert in this but you might try typing this in the terminal:

pulseaudio -k

Thanks, but it didn't help.

---

### Post by cbrunhaver on 2010-06-15
Is the pulseaudio daemon running?

---

### Post by jamesorr on 2010-06-15
> **cbrunhaver said:**
> Is the pulseaudio daemon running?

It was, but I've just managed to get it working with the following commands ...

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

---

### Post by chitowner2 on 2010-06-22
Hello folks- 

I have a somewhat related scenario: I had no audio after a clean lucid install. Dunno why this seems to be such a common issue with this distro, but that's a discussion for another time.  :-/

I fixed the audio (section 40 here: [http://kubuntuguide.org/Lucid#Sound](http://kubuntuguide.org/Lucid#Sound)) and got sound working with pulseaudio in all apps I tried.

Then I installed Audacity so I could cut segments from audio files to create ringtones for my cell phone. Had no problems with this on Karmic, but Audacity apparently won't play nice with pulseaudio and wants ALSA.

I googled up this page:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Followed those instructions and presto! no more sound anywhere.....

Now I want to undo things to restore what was working before. Unfortunately, since this was a brand-new clean install, I got no backup of the audio-working state and no idea how to cleanly reverse what that page instructed.

From that URL I got as far as 
>   Adding Users to the PulseAudio groups
Next we go to System -> Administration -> and click on Users and Groups. 

but since page is written for Gnome users and I have kubuntu, the "Users and Groups" instruction doesn't work.

Any help guys?

Thanks,
CT
:mad:

---

