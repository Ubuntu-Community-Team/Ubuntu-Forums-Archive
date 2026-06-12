---
title: "Sound disappeared on Latitude d620"
date: 2006-04-24
forum: General Help
---

### Post by mzi on 2006-04-24
Hello,

After a lot of configuration on my new Latitude d620, I figured out that /dev/dsp had disappeared. Nevertheless, sound modules were loaded:
```

snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

```
aumix says:
```

aumix:  erreur à l'ouverture du mixeur

```
Meaning it cannot open the mixer

lspci says:
```

0000:00:00.0 Host bridge: Intel Corp.: Unknown device 27a0 (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp.: Unknown device 27a2 (rev 03)
0000:00:02.1 Display controller: Intel Corp.: Unknown device 27a6 (rev 03)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corp.: Unknown device 27d2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corp.: Unknown device 27d4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b9 (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c4 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:03:01.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller (rev 40)
0000:09:00.0 Ethernet controller: Broadcom Corporation: Unknown device 1600 (rev 02)
0000:0c:00.0 Network controller: Intel Corp.: Unknown device 4222 (rev 02)

```
... in which I cannot see any soundcard.

I spare the readers and dont paste dmesg output, in which I found neither 'sound', nor 'dsp' nor 'snd'...

alsa is installed and alsaconf does not return anything useful...

Any idea?

---

