---
title: "No Sound After Crash in Lucid"
date: 2010-05-04
forum: General Help
---

### Post by z00s on 2010-05-04
So everything was working great in Lucid until my system crashed about 10 minutes ago. After booting it back up I have no sound anymore. I've got a Soundblaster Audigy that's been working in Ubuntu for years now.

Pulseaudio and Alsamixer are set how they should be (every volume meter around 80 and nothing muted).

aplay -l provides:

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0


lspci -v provides:

03:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
Subsystem: Creative Labs Device 100a
Flags: bus master, medium devsel, latency 32, IRQ 16
I/O ports at df00 [size=32]
Capabilities: <access denied>
Kernel driver in use: CA0106
Kernel modules: snd-ca0106

I even tried some unorthodox ideas such as completely shutting down via shutdown -h now. I tried killing and restarting the pulseaudio daemon. Anyone have any suggestions? I've exhausted everything I can think of / have found in trying to get the sound working again.

---

### Post by z00s on 2010-05-04
Bump.

---

### Post by slumbergod on 2010-05-04
Same for me in Xubuntu. My machine just rebooted out of the blue. When it came back no sound at all. I have tried reinstalling all the sound related packages, even recompiling the latest alsa. 

Every release of Xubuntu comes with a nasty surprise but I've always been able to nut them out. This time it looks like a clean install (that would make the fourth to get Xubuntu Lucid working properly).

---

### Post by z00s on 2010-05-06
bump.

---

### Post by XubuRoxMySox on 2010-05-11
Same story here, only from the start Xubuntu Lucid has no sound. I'd prefer to be rid of PulseAudio... I wonder if it conflicts with Alsa somehow. I have tried removing PulseAudio but it seems to want to take other essential stuff with it.

3rd Bump!

---

### Post by stinkeye on 2010-05-11
I had no sound through headphones, and couldn't fix through the normal sound preferences.
Installed gnome-alsamixer, adjusted the volume which was on zero and the sound came back.

As you can see sound preferences shows 100% while gnome-alsamixer shows the sound is turned down for headphones.

---

### Post by spylvas on 2010-05-11
hey, 

I have similar issue with my Mint 7. I ran out of the battery and my sound just died after that. I have tried to install audio related packages, but no help. All I can get is little static when sound should be played.

When booted on windows that are still on the edge of my harddrive there is sound so HW seems to be ok.

-Simo

---

### Post by GSF1200S on 2010-05-11
Wow.. random reboot out of the blue and then no sound? Crazy.. Lucid has been rough on some people..

I have Xubuntu 10.04 and I have not had any issues. The only thing I can suggest is to remove pulseaudio:
```
sudo apt-get remove pulseaudio
```
and restart the computer. Pulseaudio was a nightmare for me and has been a nightmare for many others (although for some it works fine). Pulseaudio runs on top of ALSA, so you dont need it. Dont worry about it removing ubuntu-desktop- thats just a meta package but it can be removed without removing everything on your computer. Unfortunately, it will remove the volume applet on your panel (Xfce has an ALSA mixer applet, so its not such a killer for me). If that doesnt work or the problem turns out to be something else, you can always reinstall pulseaudio.

Also, ensure that you have your sound card selected in the sound preferences, and use:
```
alsamixer
```
to ensure that no channels are muted and that you dont have any channels like pcm or master turned all the way down.

Beyond this suggestion, Ive got nothing (I know little about linux sound)...

---

### Post by eMJayy on 2010-05-14
I've been having a similar problem of the sudden loss of sound on Lucid with my *SoundBlaster Augidy SE* PCI card. However, I just found out what the issue was that was causing the problem on my machine. 

Apparently, something caused the card to switch from analog to digital output ( IEC958 ), which results in no sound being heard. The change seems to have occurred to Alsa and isn't accessible using the PulseAudio interface. 

I solved that issue by installing **Gnome Alsa Mixer** (it's in Ubuntu Software Center) and selecting *'Analog source'* from the list at the bottom of the window. That instantly corrected the issue.

---

### Post by Sepero on 2010-05-24
Right-click Sound Applet ->
Sound Preferences ->
Output (tab)

What does it say under "Choose a device for sound output"?




If simply rebooting doesn't help, try adding this line:
options snd-hda-intel probe_mask=1 model=auto

to this file:
/etc/modprobe.d/alsa-base.conf

---

### Post by ali999 on 2010-05-24
have you tried 
```
/etc/init.d/alsasound restart

```

I had an issue like this but sound started working once i restarted alsa drivers  and added it to startup applications

---

### Post by the_luke on 2010-07-14
i can confirm that installing and running gnome alsa mixer solves the problem.
i don't know the exact thing that did it, but i believe it was checking analog source.

---

### Post by Sepero on 2010-07-15
Thanks for reporting back the_luke. It's feedback like yours that really helps others.

---

### Post by dfcostal on 2010-07-27
I just had the same problem a few minutes ago. My Audigy SE was working alright and stopped after a PulseAudio crash. Got it fixed thanks to eMJayy's post.

Installing Gnome Alsa Mixer and unchecking IEC958 under the CA0106 got things back to normal. Didn't need to select "Analog source" though.

---

