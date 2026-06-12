---
title: "No sound in flash."
date: 2010-08-27
forum: General Help
---

### Post by emshains on 2010-08-27
Hello forum. 
I think I have messed up my ubuntu install pretty bad. I tried to install the latest alsa, I compiled it from source, then I couldn't boot with my custom kernel, so I used ubuntu's one. Then I deleted pulseaudio. Wine worked great, and after I reconfigured gnome (a "registry" edit with gconf-editor and gstreamer-properties) to use alsa everything was fine. Just that I couldn't listen to two streams of audio at once, e.g. I listen to rhythmbox and sound doesn't work anywhere else, even the gstreamer-properties couldn't recognize a viable alsa device. Worst of all, flash has no sound. No more youtube for me. At least I got tf2 working without any lagg in audio. 

I tried resetting everything to pulseaudio again in gstreamer-properties, I have installed and purged and installed again ubuntu-desktop package. YET, to no avail. I am aiming for a system that has sound both in wine and youtube. With the default settings, I could get sound in tf2's menu but not in-game. Could you help ? 

I am running ubuntu 10.04 x86_64, before I installed alsa from source, I was running it on a patched kernel with bfs. 

I remember in 8.04 or some newer/older release, there was a nice gnome tool for configuring which system to use for sound, now it's gone and I am left with just some nonsense (hey, it's nonsense to me) pulseaudio tool.

---

### Post by lovinglinux on 2010-08-27
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by emshains on 2010-08-28
Been there and done that. None of it helps. And I failed applying the magickal three patches.

---

