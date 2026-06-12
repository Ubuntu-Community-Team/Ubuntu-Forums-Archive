---
title: "sound card not detected in karmic"
date: 2009-12-14
forum: General Help
---

### Post by muse3332 on 2009-12-14
well basicly i  ran a command that said no sound cards found.... somebody help doesnt evrybody dessrve help plz dont foward me to a nother post plz

---

### Post by cartisdm on 2009-12-14
What sound card are you using?  Are you on a desktop or a laptop pc?

---

### Post by lidex on 2009-12-15
Did you do a clean install or was this an upgrade from Jaunty? Please post the terminal output of these commands:
```
/sbin/lsmod | grep snd
```
```
sudo lshw -C sound
```
```
aplay -l
```
```
aplay -L
```

You'll find a terminal in your Applications menu "Accessories>Terminal". Copy and paste one command at a time into terminal and hit enter key. Enter your user password where needed. Copy and paste the terminal output into your next post and for each set of data highlight the text and click on the "#" above.

---

### Post by muse3332 on 2009-12-15
/sbin/lsmod | grep snd

snd_riptide            22312  0 
snd_ac97_codec        101216  1 snd_riptide
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75488  3 snd_riptide,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           10428  1 snd_riptide
snd_hwdep               7200  1 snd_opl3_lib
snd_page_alloc          9252  2 snd_riptide,snd_pcm
gameport               11368  2 snd_riptide
snd_mpu401_uart         6972  1 snd_riptide
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  13 snd_riptide,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd





sudo lshw -C sound *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: Rockwell International
       vendor: Rockwell International
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: ioport:d000(size=64)




aplay -l
no soundcards found....

aplay -L

NOTHING HAPPEND sorry :( ok thats it i gueess

---

### Post by muse3332 on 2009-12-15
why dont you just hel me people you hover above my post and dont even bother helping? plz i wont ever post babout this topic again just plz help! evryone deserves sound!!!!!!!!

---

### Post by lidex on 2009-12-15
Do you have the sound modules installed?

Open a terminal window, and type ```
find /lib/modules/`uname -r` | grep snd
``` You should see a whole list of items come up. If you don't, it means that the upgrade process missed installing the kernel modules for sound. To fix this, type this at the command line:

```
sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
```

After installing the modules, you will need to reboot.

---

### Post by muse3332 on 2009-12-15
ok a huge list came up with some word in red... so im guessing they are installed so what can i do now?

---

### Post by lidex on 2009-12-15
Post the output of the first command. Highlight the text then copy and paste. Now highlight in this editor and click the "#" above to enclose in code tags.

---

### Post by muse3332 on 2009-12-16
david1@david-desktop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.31-16-generic-pae/kernel/sound/oss/msnd.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/msnd
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-twl4030.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-hrtimer.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.31-16-generic-pae/kernel/sound/synth/emux/snd-emux-synth.ko

---

### Post by lidex on 2009-12-16
What was in red?

Run these commands, one at a time, in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now reboot. If that doesn't help try enabling backports in "System>Administration>Software Sources" on the "Updates" tab and running those commands again. Reboot.

---

### Post by lidex on 2009-12-16
muse3332, what's this pae kernel?

---

### Post by muse3332 on 2009-12-16
ha sorry but i have no idea.. and i did what you told me but none of it worked..

---

### Post by muse3332 on 2009-12-18
hello?

---

