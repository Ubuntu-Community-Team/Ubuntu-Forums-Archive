---
title: "Karmic: udev creates certain devices in wrong path"
date: 2009-10-31
forum: General Help
---

### Post by atterdag on 2009-10-31
I've just upgraded my mythbuntu from jaunty to karmic.

I can see udev is not creating my sound and tuner devices in the right path. The sound devices nodes should be in /dev/snd/.. but are just in /dev and the dvb devices should also be in /dev/dvb/ but are also just in /dev.

I could workaround the problem with the tuners, by just changing the device path in the mythtv database, but I can't get any sound because there are just to many dependencies to the /dev/snd path. For instance not even alsamixer can find any sound card.

If I run a udevadm monitor while modprobing the snd-intel8x0 modules (my sndcard is a nForce4 CK804 onboard card), then I get the following output.

```
KERNEL[1256999061.186018] add      /module/snd_page_alloc (module)
KERNEL[1256999061.189422] add      /module/soundcore (module)
KERNEL[1256999061.189679] add      /class/sound (class)
UDEV  [1256999061.208315] add      /module/snd_page_alloc (module)
UDEV  [1256999061.210184] add      /module/soundcore (module)
UDEV  [1256999061.211492] add      /class/sound (class)
KERNEL[1256999061.211987] add      /module/snd (module)
UDEV  [1256999061.213130] add      /module/snd (module)
KERNEL[1256999061.222290] add      /module/snd_seq_device (module)
KERNEL[1256999061.228746] add      /module/snd_timer (module)
KERNEL[1256999061.229079] add      /devices/virtual/sound/timer (sound)
UDEV  [1256999061.241741] add      /module/snd_seq_device (module)
UDEV  [1256999061.242922] add      /module/snd_timer (module)
KERNEL[1256999061.248298] add      /module/snd_seq (module)
UDEV  [1256999061.249628] add      /module/snd_seq (module)
UDEV  [1256999061.250770] add      /devices/virtual/sound/timer (sound)
KERNEL[1256999061.251321] add      /devices/virtual/sound/seq (sound)
KERNEL[1256999061.261203] add      /module/snd_seq_midi_event (module)
UDEV  [1256999061.262529] add      /module/snd_seq_midi_event (module)
UDEV  [1256999061.276706] add      /devices/virtual/sound/seq (sound)
KERNEL[1256999061.277332] add      /module/snd_rawmidi (module)
UDEV  [1256999061.278498] add      /module/snd_rawmidi (module)
KERNEL[1256999061.287387] add      /module/snd_seq_midi (module)
UDEV  [1256999061.288715] add      /module/snd_seq_midi (module)
KERNEL[1256999061.299027] add      /module/snd_seq_oss (module)
KERNEL[1256999061.299088] add      /devices/virtual/sound/sequencer (sound)
KERNEL[1256999061.299121] add      /devices/virtual/sound/sequencer2 (sound)
UDEV  [1256999061.300387] add      /module/snd_seq_oss (module)
KERNEL[1256999061.312925] add      /module/snd_seq_dummy (module)
UDEV  [1256999061.314762] add      /module/snd_seq_dummy (module)
UDEV  [1256999061.316429] add      /devices/virtual/sound/sequencer (sound)
UDEV  [1256999061.317466] add      /devices/virtual/sound/sequencer2 (sound)
KERNEL[1256999061.344157] add      /module/snd_pcm (module)
UDEV  [1256999061.345629] add      /module/snd_pcm (module)
KERNEL[1256999061.353375] add      /module/snd_mixer_oss (module)
KERNEL[1256999061.361341] add      /module/snd_pcm_oss (module)
UDEV  [1256999061.362627] add      /module/snd_mixer_oss (module)
UDEV  [1256999061.364182] add      /module/snd_pcm_oss (module)
KERNEL[1256999061.373535] add      /module/ac97_bus (module)
KERNEL[1256999061.373595] add      /bus/ac97 (bus)
KERNEL[1256999061.374065] add      /module/snd_ac97_codec (module)
UDEV  [1256999061.379566] add      /module/ac97_bus (module)
UDEV  [1256999061.380775] add      /bus/ac97 (bus)
UDEV  [1256999061.381872] add      /module/snd_ac97_codec (module)
KERNEL[1256999061.386460] add      /module/snd_intel8x0 (module)
UDEV  [1256999061.387678] add      /module/snd_intel8x0 (module)
KERNEL[1256999061.712429] add      /devices/pci0000:00/0000:00:04.0/sound/card0 (sound)
UDEV  [1256999061.713775] add      /devices/pci0000:00/0000:00:04.0/sound/card0 (sound)
KERNEL[1256999061.714328] add      /devices/pci0000:00/0000:00:04.0/sound/card0/pcmC0D2p (sound)
KERNEL[1256999061.719111] add      /devices/pci0000:00/0000:00:04.0/sound/card0/pcmC0D1c (sound)
UDEV  [1256999061.724023] add      /devices/pci0000:00/0000:00:04.0/sound/card0/pcmC0D1c (sound)
KERNEL[1256999061.724421] add      /devices/pci0000:00/0000:00:04.0/sound/card0/adsp (sound)
KERNEL[1256999061.728852] add      /devices/pci0000:00/0000:00:04.0/sound/card0/pcmC0D0p (sound)
KERNEL[1256999061.733664] add      /devices/pci0000:00/0000:00:04.0/sound/card0/pcmC0D0c (sound)
KERNEL[1256999061.733975] add      /devices/pci0000:00/0000:00:04.0/sound/card0/dsp (sound)
KERNEL[1256999061.734156] add      /devices/pci0000:00/0000:00:04.0/sound/card0/audio (sound)
KERNEL[1256999061.734334] add      /devices/pci0000:00/0000:00:04.0/0-0:ALC850 (ac97)
KERNEL[1256999061.734508] add      /devices/pci0000:00/0000:00:04.0/sound/card0/controlC0 (sound)
KERNEL[1256999061.734698] add      /devices/pci0000:00/0000:00:04.0/sound/card0/mixer (sound)
KERNEL[1256999061.735526] add      /bus/pci/drivers/Intel ICH (drivers)
UDEV  [1256999061.737915] add      /devices/pci0000:00/0000:00:04.0/sound/card0/adsp (sound)
UDEV  [1256999061.738955] add      /devices/pci0000:00/0000:00:04.0/sound/card0/pcmC0D0p (sound)
UDEV  [1256999061.748378] add      /devices/pci0000:00/0000:00:04.0/sound/card0/dsp (sound)
UDEV  [1256999061.753495] add      /devices/pci0000:00/0000:00:04.0/sound/card0/audio (sound)
UDEV  [1256999061.754695] add      /devices/pci0000:00/0000:00:04.0/sound/card0/pcmC0D2p (sound)
UDEV  [1256999061.755717] add      /devices/pci0000:00/0000:00:04.0/sound/card0/pcmC0D0c (sound)
UDEV  [1256999061.757411] add      /devices/pci0000:00/0000:00:04.0/0-0:ALC850 (ac97)
UDEV  [1256999061.761299] add      /bus/pci/drivers/Intel ICH (drivers)
UDEV  [1256999061.766297] add      /devices/pci0000:00/0000:00:04.0/sound/card0/mixer (sound)
KERNEL[1256999061.766912] change   /devices/pci0000:00/0000:00:04.0/sound/card0 (sound)
UDEV  [1256999061.782137] add      /devices/pci0000:00/0000:00:04.0/sound/card0/controlC0 (sound)
UDEV  [1256999061.796437] change   /devices/pci0000:00/0000:00:04.0/sound/card0 (sound)

```

So the module is loaded and udev creates the devices; just in the wrong place.

Does anyone have an idea what gives?

---

