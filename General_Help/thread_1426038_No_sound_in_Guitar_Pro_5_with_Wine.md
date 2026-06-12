---
title: "No sound in Guitar Pro 5 with Wine"
date: 2010-03-09
forum: General Help
---

### Post by acalora on 2010-03-09
Hey, this problem's just started, and I'm not sure what caused it, but for some reason, when I open Guitar Pro 5 in Wine (v1.1.40), there is no sound. I go into the audio settings to select Timidity, but it's not listed. I do have it installed and I can launch commands such as 'timidity anything.mid' to get it to play midi's, but other than that, it doesn't work. 

When I run Wine and launch Guitar Pro 5, I get this output:

```
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
ALSA lib pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mciwave:MCIWAVE_DriverProc Unsupported yet command [2115]
ALSA lib pcm.c:7234:(snd_pcm_recover) underrun occured

```I would appreciate any help, thank you.

---

### Post by uRock on 2010-03-09
No Peavey?:guitar:

---

### Post by Bradj47 on 2010-03-09
> **acalora said:**
> Hey, this problem's just started, and I'm not sure what caused it, but for some reason, when I open Guitar Pro 5 in Wine (v1.1.40), there is no sound. I go into the audio settings to select Timidity, but it's not listed. I do have it installed and I can launch commands such as 'timidity anything.mid' to get it to play midi's, but other than that, it doesn't work. 

When I run Wine and launch Guitar Pro 5, I get this output:

```
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
ALSA lib pcm_dmix.c:947:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mciwave:MCIWAVE_DriverProc Unsupported yet command [2115]
ALSA lib pcm.c:7234:(snd_pcm_recover) underrun occured

```I would appreciate any help, thank you.

Sounds to me like WinE's having trouble opening a needed library. But that's all I can say. Perhaps there's a WinE expert here that can help. Do other programs that use sound work? If so then it's a problem with Guitar Pro 5. If not then it's a problem with WinE.

---

### Post by acalora on 2010-03-09
Do you mean the amplification? If so, no, if otherwise, I'm not sure what you mean.

---

### Post by Bradj47 on 2010-03-09
> **acalora said:**
> Do you mean the amplification? If so, no, if otherwise, I'm not sure what you mean.

No, I'm asking if you can run other programs besides Guitar Pro 5 on WinE and have the sound work.

---

### Post by acalora on 2010-03-09
Well, the sound in my recording program, GoldWave, doesn't. But my RSE in Guitar Pro 5 works and plays, except it really sounds horrible, which is why I want to use MIDI.

---

### Post by acalora on 2010-03-09
Sorry, iRock said above 'No Peavey?'
I was responding to him.

---

### Post by acalora on 2010-03-10
Bump

---

### Post by Lennon V C on 2010-04-18
Guitar Pro 6 has native support for Ubuntu BTW. You can upgrade your licence for $30.

---

### Post by 9000 Internets on 2010-04-18
Or you can use tuxguitar. It's worked for me.

---

