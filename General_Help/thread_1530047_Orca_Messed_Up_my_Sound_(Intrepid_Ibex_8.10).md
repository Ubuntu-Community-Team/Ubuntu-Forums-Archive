---
title: "Orca Messed Up my Sound (Intrepid Ibex 8.10)"
date: 2010-07-13
forum: General Help
---

### Post by Smacks on 2010-07-13
I had Orca installed for absolutely no reason, and I decided to start it and try playing with the text to speech. It wasn't interesting and I closed it. Now that I've restarted the computer, in GNOME sound doesn't work for certain things (VLC, Firefox). I uninstalled Orca because it auto-started on log-in and the preferences would freeze when I tried to change them.

I read about a problem in 9.10 where there is some file taht disabled pulseaudio, I don't see it and I am using 8.10 anyways. :/ 

Please help me, I'd really like to have consistent sound without using a different DE.

Thanks in advance

EDIT: I've re-installed Orca and edited the preferences fine this time, but the sound still doesn't work for VLC and Firefox. Now I've completely uninstalled Orca from synaptic and it still doesn't work. The sound test works fine, though. I'm sure there is some configuration file Orca added something to, but I don't know how to find it.

---

### Post by Smacks on 2010-07-22
Anyone there?

---

### Post by Smacks on 2010-07-22
in the file /home/sma/.pulse/volume-restore.table, I noticed all the things that don't work (firefox, totem sound preview, vlc) have an 'rtp' on them. Could that mean something? I'd like if someone helped me out.

---

### Post by Smacks on 2010-07-22
I deleted the rtps from the file above, and sound works, but I can't play multiple sounds. I read a short bit after finally finding something about rtp and it seems it enables mulyiplr things to play,so I'll try just deleting the espeak from the file, see if that works.

---

### Post by Smacks on 2010-07-22
Here is the volume-restore.table file so far:

```
pulsecore/protocol-native.c$python
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$Audacious
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [skype]
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0
alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$Banshee
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [swami]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [nst]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [python2.5]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$Pidgin
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [cheese]


alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$Cheese
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [VisualBoyAdvance]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$Rhythmbox
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [firefox (deleted)]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$gnobots2
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$iagno
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$gnibbles
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$OSS Emulation[espeak-synthesis-driver.bin]
1 65536
#rtp
alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$Totem Movie Player
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [wine-preloader]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0
alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$gnometris
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$gnect
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [canberra-gtk-play]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [gnome-sound-recorder]


alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$Power Manager
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [aplay]
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$gnome-sound-recorder
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [firefox]
2 65536 65536
#rtp
alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$totem-plugin-viewer
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-esound.c$mozillaSound
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [gnome-sound-properties]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0
alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$gnome-sound-properties
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0
alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$ALSA plug-in [zsnes]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [dosbox]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [vlc]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$Songbird
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$totem-audio-preview
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [songbird-bin]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [artsd]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [kino]
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$pitivi
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$Test stream
1 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$milkytracker
2 65536 65536
alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0

```

---

### Post by Smacks on 2010-08-04
VLC seems to just be screwing everything up, if vlc is running nothing else will play sound. Is it really anything to do with the .table file?

While vlc is running and I do a sound test I get ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused
```

Maybe someone can respond now that I am a little more specific: VLC is hogging the sound, how do I change this?

---

