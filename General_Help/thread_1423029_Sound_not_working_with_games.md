---
title: "Sound not working with games"
date: 2010-03-06
forum: General Help
---

### Post by MindFusion on 2010-03-06
Hi everyone

I already posted a topic about this but i got wrongly interpreted as someone gave me a link to a topic to restore your audio fully, which isn't necessairy, as I AM able to play music through rythmbox, on dvd's, on youtube... but not on games.

I have a conexant Hi-Def audio on a HP laptop here, and when i typed in the code 'aplay -l' in the terminal, i got this:

[CODE]jakob@jakob-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jakob@jakob-laptop:~$ ^C
/CODE]

As you can see my conexantaudio driver is listed, but it does not seem to work with games... anyone any ideas? I have 9.10 and in 9.04 it did work..

---

### Post by Intrepid Ibex on 2010-03-06
Audio doesn't work with wine for you? Did you check out winecfg (Configure Wine or something like that in the menu) -> Audio -> Verify you got ALSA Driver, Full Hardware Acceleration, 44100 as teh Default Sample Rate and 16 Bits Per Sample as default (the qualities)?

You can also test the audio with the "Test Sound" button from there.

Clarification:

[img]http://www.tipotheday.com/wp-content/uploads/2007/09/winecfg-audio.png[/img]

---

### Post by dineshnandana.wije on 2010-03-06
Please open add/remove..
and type here "wine"
Install wine
And later Visit :[http://www.winehq.org]("http://www.winehq.org")
and install other softwares
install your driver with wine....

---

### Post by MindFusion on 2010-03-09
I did NOT ask Wine, I'm smart enough to configure that myself... I meant games in general..

---

