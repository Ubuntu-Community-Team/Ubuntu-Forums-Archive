---
title: "Issues with sound, terminal out put included."
date: 2012-02-10
forum: General Help
---

### Post by archx on 2012-02-10
So iv been troubleshooting, looking all over the internet, following advice but i cant get my xubuntu sound to work. I followed the advice on [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)   but im alittle overwhelmed by it all. So here are the reports from the first stage.

Does anyone understand this enough to tell me if and what the problem is???

```

archx@archx:~$ sudo aplay -l
[sudo] password for archx: 
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: VT82xx [HDA VIA VT82xx], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: VT82xx [HDA VIA VT82xx], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
archx@archx:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-adlib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-als100.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-sgalaxy.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/msnd
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-azt2320.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4231-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-dt019x.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-cmi8330.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-opl3sa2.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-es18xx.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb16.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sbawe.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-es968.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb8.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb-common.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/es1688/snd-es1688.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-sscape.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/snd-sc6000.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/gus/snd-interwave.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/gus/snd-gusmax.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/snd-mts64.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/snd-virmidi.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/snd-portman2x4.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/snd-serial-u16550.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/snd-aloop.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/snd-dummy.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/drivers/snd-mtpav.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-intel8x0.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-rme96.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-ens1371.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/trident/snd-trident.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/mixart/snd-mixart.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-maestro3.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-als4000.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-rme32.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-als300.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-cmipci.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-via82xx.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-atiixp-modem.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-azt3328.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-cs4281.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-es1938.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-intel8x0m.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/nm256/snd-nm256.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/pdplus/snd-pdplus.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-sonicvibes.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-ens1370.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-es1968.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/riptide/snd-riptide.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-fm801.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-atiixp.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-via82xx-modem.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-bt87x.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-sis7019.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-ad1889.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/snd-cs5530.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/pci/vx222/snd-vx222.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/soc/snd-soc-core.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/synth/snd-util-mem.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/i2c/snd-i2c.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/i2c/snd-cs8427.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/i2c/snd-tea6330t.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/i2c/other/snd-pt2258.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4117.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4114.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/usb/snd-usb-audio.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/usb/snd-usb-lib.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/snd.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/snd-page-alloc.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-device.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-virmidi.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-dummy.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/snd-rtctimer.ko
/lib/modules/2.6.24-30-generic/ubuntu/sound/alsa-driver/acore/snd-rawmidi.ko
/lib/modules/2.6.24-30-generic/ubuntu/snd-bt-sco.ko
archx@archx:~$ lspci -v | grep -A7 -i "audio"
02:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at dfafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
    Subsystem: Unknown device 1631:e028
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>


```
Let me know if you get anything.

---

