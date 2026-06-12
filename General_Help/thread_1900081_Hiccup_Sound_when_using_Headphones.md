---
title: "Hiccup Sound when using Headphones"
date: 2011-12-25
forum: General Help
---

### Post by juanma268 on 2011-12-25
Hello forum people!

I have installed Ubuntu 11.10 but the computer has a problem with the audio output.

This is the problem: the sound only works when the balance is only for left or right speaker (also with headphones). When configuring the sound properties to play for the middle, the audio has hiccup, I mean, the sound is no continous. It happens when i am playing audio and video files. I can listen to music by just one side in headphones but is really annoying :(, for speakers works fine (both sides works in only left or right).

I have tried with VLC, Banshee and Totem players, but nothing yet has worked.

When the headphones are plugged and I am setting the audio properties, in the "connector" combo box of the "out" tag, the selected option changes by itself between "analogic output" and "analogic headphones" without stopping.

I am using the Duplex Analogic Stereo´s profile in hardware tag, the others profile work fine (for one side of speaker), except the IEC958.

My motherboard is an Intel 82801GB/GR and the sound card is an Intel N10/ICH 7.

Thanks in advance for your help.

---

### Post by juanma268 on 2011-12-27
Hello again, there is someone there?

---

### Post by vangop on 2011-12-27
would be nice to see some screenshots to understand better..
The sound on linux is a mess, most likely you need to play with the settings in:
1. sound properties
2. gstreamer-properties
3. alsamixer (run from terminal)

---

### Post by juanma268 on 2011-12-28
Something funny happened when i was taking the snapshots. When I pressed the button of print-screen the sound of the mp3 file, that i was listening on Banshee, turns into noisy. I am thinking that the problem its about a hard disk reading issue :-k

These are the snapshots:

[ATTACH]209839[/ATTACH]
[ATTACH]209840[/ATTACH]

---

