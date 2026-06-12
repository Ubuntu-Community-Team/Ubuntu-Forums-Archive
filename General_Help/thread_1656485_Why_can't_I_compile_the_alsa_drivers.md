---
title: "Why can't I compile the alsa drivers?"
date: 2010-12-31
forum: General Help
---

### Post by HalfEmptyHero on 2010-12-31
I'm trying to compile the alsa drivers so I can get alsaconf and hopefully fix some of the sound problems I have, however I always get some errors on make. When I do ./configure --with-cards=hda-intel, I don't get any errors however when I try to do make, this is what I get.

```
$ make
make dep
make[1]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/include'
make -C sound prepare
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/include/sound'
make .includes.tmp
make[4]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/include/sound'
make[4]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/include/sound'
make prepare2
make[4]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/include/sound'
cp ../../alsa-kernel/include/ac97_codec.h .
patch -p0 -i ac97_codec.patch ac97_codec.h
patching file ac97_codec.h
ln -s ../../alsa-kernel/include/aci.h
ln -s ../../alsa-kernel/include/ad1816a.h
ln -s ../../alsa-kernel/include/ad1843.h
ln -s ../../alsa-kernel/include/ak4113.h
ln -s ../../alsa-kernel/include/ak4114.h
ln -s ../../alsa-kernel/include/ak4117.h
ln -s ../../alsa-kernel/include/ak4531_codec.h
ln -s ../../alsa-kernel/include/ak4xxx-adda.h
ln -s ../../alsa-kernel/include/asequencer.h
ln -s ../../alsa-kernel/include/asound.h
ln -s ../../alsa-kernel/include/asound_fm.h
ln -s ../../alsa-kernel/include/asoundef.h
ln -s ../../alsa-kernel/include/atmel-abdac.h
ln -s ../../alsa-kernel/include/atmel-ac97c.h
ln -s ../../alsa-kernel/include/control.h
cp ../../alsa-kernel/include/core.h .
patch -p0 -i core.patch core.h
patching file core.h
ln -s ../../alsa-kernel/include/cs4231-regs.h
ln -s ../../alsa-kernel/include/cs46xx.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_scb_types.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_spos.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_task_types.h
ln -s ../../alsa-kernel/include/cs8403.h
ln -s ../../alsa-kernel/include/cs8427.h
ln -s ../../alsa-kernel/include/emu10k1.h
ln -s ../../alsa-kernel/include/emu10k1_synth.h
ln -s ../../alsa-kernel/include/emu8000.h
ln -s ../../alsa-kernel/include/emu8000_reg.h
ln -s ../../alsa-kernel/include/emux_legacy.h
ln -s ../../alsa-kernel/include/emux_synth.h
ln -s ../../alsa-kernel/include/es1688.h
ln -s ../../alsa-kernel/include/gus.h
ln -s ../../alsa-kernel/include/hda_hwdep.h
ln -s ../../alsa-kernel/include/hdsp.h
ln -s ../../alsa-kernel/include/hdspm.h
ln -s ../../alsa-kernel/include/hwdep.h
ln -s ../../alsa-kernel/include/i2c.h
ln -s ../../alsa-kernel/include/info.h
ln -s ../../alsa-kernel/include/initval.h
ln -s ../../alsa-kernel/include/jack.h
ln -s ../../alsa-kernel/include/l3.h
ln -s ../../alsa-kernel/include/memalloc.h
ln -s ../../alsa-kernel/include/minors.h
ln -s ../../alsa-kernel/include/mixer_oss.h
ln -s ../../alsa-kernel/include/mpu401.h
ln -s ../../alsa-kernel/include/opl3.h
ln -s ../../alsa-kernel/include/opl4.h
ln -s ../../alsa-kernel/include/pcm-indirect.h
cp ../../alsa-kernel/include/pcm.h .
patch -p0 -i pcm.patch pcm.h
patching file pcm.h
ln -s ../../alsa-kernel/include/pcm_oss.h
ln -s ../../alsa-kernel/include/pcm_params.h
ln -s ../../alsa-kernel/include/pt2258.h
ln -s ../../alsa-kernel/include/pxa2xx-lib.h
ln -s ../../alsa-kernel/include/rawmidi.h
ln -s ../../alsa-kernel/include/s3c24xx_uda134x.h
ln -s ../../alsa-kernel/include/sb.h
ln -s ../../alsa-kernel/include/sb16_csp.h
ln -s ../../alsa-kernel/include/seq_device.h
ln -s ../../alsa-kernel/include/seq_kernel.h
ln -s ../../alsa-kernel/include/seq_midi_emul.h
ln -s ../../alsa-kernel/include/seq_midi_event.h
ln -s ../../alsa-kernel/include/seq_oss.h
ln -s ../../alsa-kernel/include/seq_oss_legacy.h
ln -s ../../alsa-kernel/include/seq_virmidi.h
ln -s ../../alsa-kernel/include/sfnt_info.h
ln -s ../../alsa-kernel/include/sh_dac_audio.h
ln -s ../../alsa-kernel/include/sh_fsi.h
ln -s ../../alsa-kernel/include/snd_wavefront.h
ln -s ../../alsa-kernel/include/soc-dai.h
ln -s ../../alsa-kernel/include/soc-dapm.h
ln -s ../../alsa-kernel/include/soc-of-simple.h
ln -s ../../alsa-kernel/include/soc.h
ln -s ../../alsa-kernel/include/soundfont.h
ln -s ../../alsa-kernel/include/tea575x-tuner.h
ln -s ../../alsa-kernel/include/tea6330t.h
ln -s ../../alsa-kernel/include/timer.h
ln -s ../../alsa-kernel/include/tlv.h
ln -s ../../alsa-kernel/include/tlv320dac33-plat.h
ln -s ../../alsa-kernel/include/tpa6130a2-plat.h
ln -s ../../alsa-kernel/include/trident.h
ln -s ../../alsa-kernel/include/uda134x.h
ln -s ../../alsa-kernel/include/uda1380.h
ln -s ../../alsa-kernel/include/util_mem.h
ln -s ../version.h
ln -s ../../alsa-kernel/include/vx_core.h
ln -s ../../alsa-kernel/include/wavefront.h
ln -s ../../alsa-kernel/include/wm2000.h
ln -s ../../alsa-kernel/include/wm8903.h
ln -s ../../alsa-kernel/include/wm8904.h
ln -s ../../alsa-kernel/include/wm8955.h
ln -s ../../alsa-kernel/include/wm8960.h
ln -s ../../alsa-kernel/include/wm8993.h
ln -s ../../alsa-kernel/include/wm9081.h
ln -s ../../alsa-kernel/include/wss.h
ln -s ../../alsa-kernel/include/ymfpci.h
make[4]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/include/sound'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/include/sound'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/include'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #2 succeeded at 90 (offset 1 line).
Hunk #3 succeeded at 162 (offset 1 line).
Hunk #4 succeeded at 496 (offset 13 lines).
Hunk #5 succeeded at 536 (offset 13 lines).
Hunk #6 succeeded at 952 (offset 13 lines).
Hunk #7 succeeded at 992 (offset 13 lines).
Hunk #8 succeeded at 1026 (offset 13 lines).
copying file alsa-kernel/core/pcm.c
patching file pcm.c
Hunk #2 succeeded at 934 (offset 5 lines).
Hunk #3 succeeded at 950 (offset 5 lines).
Hunk #4 succeeded at 962 (offset 5 lines).
Hunk #5 succeeded at 1018 (offset 5 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
copying file alsa-kernel/core/pcm_memory.c
patching file pcm_memory.c
Hunk #2 succeeded at 452 (offset 1 line).
copying file alsa-kernel/core/control.c
patching file control.c
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #3 succeeded at 308 (offset 1 line).
copying file alsa-kernel/core/init.c
patching file init.c
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #4 succeeded at 191 (offset 3 lines).
Hunk #5 succeeded at 269 (offset 3 lines).
Hunk #6 succeeded at 281 (offset 3 lines).
Hunk #7 succeeded at 298 (offset 3 lines).
Hunk #8 succeeded at 322 (offset 3 lines).
Hunk #9 succeeded at 377 (offset 3 lines).
Hunk #10 succeeded at 388 (offset 3 lines).
Hunk #11 succeeded at 414 (offset 3 lines).
Hunk #12 succeeded at 521 (offset 3 lines).
copying file alsa-kernel/core/timer.c
patching file timer.c
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
copying file alsa-kernel/core/misc.c
patching file misc.c
Hunk #2 succeeded at 49 (offset 1 line).
Hunk #3 succeeded at 150 (offset 1 line).
copying file alsa-kernel/core/hrtimer.c
patching file hrtimer.c
Hunk #2 succeeded at 67 (offset 1 line).
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore/oss'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #2 succeeded at 59 (offset 2 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 250 (offset 2 lines).
make[4]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
Hunk #3 succeeded at 192 (offset 3 lines).
Hunk #4 succeeded at 227 (offset 4 lines).
Hunk #5 succeeded at 330 (offset 4 lines).
make[4]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore/seq/oss'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore/seq'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/acore'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/i2c'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/i2c/l3'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/i2c/l3'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/i2c/other'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/i2c/other'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/i2c'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
Hunk #2 succeeded at 835 (offset 1 line).
Hunk #3 succeeded at 1094 (offset 1 line).
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
Hunk #2 succeeded at 612 (offset 1 line).
Hunk #3 succeeded at 883 (offset 1 line).
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #2 succeeded at 438 (offset 2 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/opl3'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/opl4'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/opl4'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/pcsp'
copying file alsa-kernel/drivers/pcsp/pcsp.c
patching file pcsp.c
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/vx'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers/vx'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/drivers'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/ad1848'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/ad1848'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/cs423x'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/cs423x'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/es1688'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/es1688'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/gus'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/gus'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/msnd'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/msnd'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #2 succeeded at 712 (offset 2 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/sb'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
Hunk #2 succeeded at 251 (offset -3 lines).
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
Hunk #2 succeeded at 1947 (offset 1 line).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/wavefront'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/wss'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa/wss'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/isa'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/synth'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/synth/emux'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/synth/emux'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/synth'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1680 (offset 9 lines).
Hunk #3 succeeded at 1725 (offset 9 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1313 (offset 6 lines).
Hunk #3 succeeded at 1356 (offset 6 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 850 (offset 4 lines).
Hunk #3 succeeded at 1004 (offset 4 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3142 (offset -34 lines).
Hunk #3 succeeded at 3437 (offset -34 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2121 (offset -10 lines).
Hunk #3 succeeded at 2497 (offset -10 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #3 succeeded at 1434 (offset 5 lines).
Hunk #4 succeeded at 1624 (offset 14 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #3 succeeded at 715 (offset 9 lines).
Hunk #4 succeeded at 725 (offset 9 lines).
Hunk #5 succeeded at 3288 (offset 160 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2500 (offset 6 lines).
Hunk #3 succeeded at 2510 (offset 6 lines).
Hunk #4 succeeded at 2525 (offset 6 lines).
Hunk #5 succeeded at 2536 (offset 6 lines).
Hunk #6 succeeded at 2547 (offset 6 lines).
Hunk #7 succeeded at 2630 (offset 6 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1187 (offset 7 lines).
Hunk #3 succeeded at 1247 (offset 7 lines).
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #3 succeeded at 1928 (offset 10 lines).
Hunk #4 succeeded at 1940 (offset 10 lines).
Hunk #5 succeeded at 1964 (offset 10 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ac97'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2148 (offset -57 lines).
Hunk #3 succeeded at 2318 (offset -57 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ali5451'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/asihpi'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/asihpi'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 339 (offset -2 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/au88x0'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/aw2'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/aw2'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1636 (offset 73 lines).
Hunk #4 succeeded at 1908 (offset 83 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ca0106'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ctxfi'
copying file alsa-kernel/pci/ctxfi/ctatc.c
patching file ctatc.c
Hunk #2 succeeded at 1238 (offset -10 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1945 (offset 2 lines).
Hunk #2 succeeded at 2017 (offset 2 lines).
Hunk #3 succeeded at 2252 (offset 1 line).
Hunk #4 succeeded at 2260 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/indigodjx.c
patching file indigodjx.c
Hunk #2 succeeded at 112 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/indigoiox.c
patching file indigoiox.c
Hunk #2 succeeded at 114 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
Hunk #2 succeeded at 125 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #4 succeeded at 1409 (offset -1 lines).
Hunk #5 succeeded at 1452 (offset -1 lines).
Hunk #6 succeeded at 1767 (offset 3 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 941 (offset 1 line).
Hunk #3 succeeded at 1634 (offset 6 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/hda'
copying file alsa-kernel/pci/hda/hda_intel.c
patching file hda_intel.c
Hunk #2 succeeded at 2360 (offset 7 lines).
Hunk #3 succeeded at 2376 (offset 8 lines).
Hunk #4 succeeded at 2392 (offset 8 lines).
Hunk #5 succeeded at 2405 (offset 8 lines).
Hunk #6 succeeded at 2526 (offset 8 lines).
copying file alsa-kernel/pci/hda/hda_beep.c
patching file hda_beep.c
Hunk #2 succeeded at 95 (offset 1 line).
Hunk #3 succeeded at 123 with fuzz 2 (offset 1 line).
Hunk #4 succeeded at 141 (offset 1 line).
Hunk #5 succeeded at 163 (offset 1 line).
Hunk #6 succeeded at 282 with fuzz 2 (offset 18 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/hda'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ice1712'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ice1712'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2344 (offset 5 lines).
Hunk #3 succeeded at 2500 (offset 5 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/korg1212'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/mixart'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/mixart'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/nm256'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/nm256'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/oxygen'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/oxygen'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/pdplus'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/pdplus'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #3 succeeded at 2221 (offset 3 lines).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/riptide'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/rme9652'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/rme9652'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/trident'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/trident'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/vx222'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/vx222'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci/ymfpci'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pci'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/codecs'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/codecs'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/core'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/core'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/soundbus'
make[4]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa/soundbus'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/aoa'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc'
copying file alsa-kernel/soc/soc-core.c
patching file soc-core.c
Hunk #2 succeeded at 1331 (offset 90 lines).
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/atmel'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/atmel'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/au1x'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/au1x'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/blackfin'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/blackfin'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/codecs'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/codecs'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/davinci'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/davinci'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/fsl'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/fsl'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/imx'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/imx'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/omap'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/omap'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/pxa'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/pxa'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/s6000'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/s6000'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/sh'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/sh'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/txx9'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc/txx9'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/soc'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/usb'
copying file alsa-kernel/usb/card.c
patching file card.c
copying file alsa-kernel/usb/endpoint.c
patching file endpoint.c
Hunk #2 succeeded at 187 (offset 2 lines).
Hunk #3 succeeded at 278 (offset 2 lines).
Hunk #4 succeeded at 309 (offset 2 lines).
copying file alsa-kernel/usb/helper.c
patching file helper.c
Hunk #2 succeeded at 93 (offset 1 line).
copying file alsa-kernel/usb/quirks.c
patching file quirks.c
Hunk #2 succeeded at 161 (offset 2 lines).
Hunk #3 succeeded at 236 (offset 2 lines).
Hunk #4 succeeded at 325 (offset 2 lines).
Hunk #5 succeeded at 343 (offset 2 lines).
Hunk #6 succeeded at 357 (offset 2 lines).
Hunk #7 succeeded at 370 (offset 2 lines).
copying file alsa-kernel/usb/urb.c
patching file urb.c
Hunk #2 succeeded at 72 (offset 1 line).
Hunk #3 succeeded at 87 (offset 1 line).
Hunk #4 succeeded at 171 (offset 1 line).
Hunk #5 succeeded at 198 (offset 1 line).
Hunk #6 succeeded at 350 (offset 1 line).
copying file alsa-kernel/usb/midi.c
patching file midi.c
Hunk #6 succeeded at 1004 with fuzz 1.
Hunk #7 succeeded at 1021 (offset 2 lines).
Hunk #8 succeeded at 1031 (offset 2 lines).
Hunk #9 succeeded at 1749 (offset 12 lines).
Hunk #10 succeeded at 2120 (offset 12 lines).
copying file alsa-kernel/usb/mixer.c
patching file mixer.c
copying file alsa-kernel/usb/mixer_quirks.c
patching file mixer_quirks.c
Hunk #2 succeeded at 64 (offset 1 line).
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/usb/caiaq'
copying file alsa-kernel/usb/caiaq/audio.c
patching file audio.c
Hunk #2 succeeded at 465 (offset 1 line).
Hunk #3 succeeded at 528 (offset 1 line).
copying file alsa-kernel/usb/caiaq/device.c
patching file device.c
Hunk #2 succeeded at 139 (offset 7 lines).
Hunk #3 succeeded at 401 (offset 7 lines).
copying file alsa-kernel/usb/caiaq/input.c
patching file input.c
Hunk #2 succeeded at 21 with fuzz 1 (offset 1 line).
Hunk #3 succeeded at 301 (offset 1 line).
Hunk #4 succeeded at 322 (offset 1 line).
Hunk #5 succeeded at 364 (offset 1 line).
Hunk #6 succeeded at 378 (offset 1 line).
Hunk #7 succeeded at 507 (offset 1 line).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/usb/caiaq'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/usb/misc'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/usb/misc'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #2 succeeded at 33 (offset 1 line).
Hunk #3 succeeded at 56 (offset 1 line).
Hunk #4 succeeded at 142 (offset 1 line).
Hunk #5 succeeded at 181 (offset 1 line).
Hunk #6 succeeded at 237 (offset 1 line).
Hunk #7 succeeded at 290 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
Hunk #2 succeeded at 174 (offset 1 line).
Hunk #3 succeeded at 190 (offset 1 line).
Hunk #4 succeeded at 254 (offset 1 line).
Hunk #5 succeeded at 267 (offset 1 line).
Hunk #6 succeeded at 313 (offset 1 line).
Hunk #7 succeeded at 377 (offset 1 line).
Hunk #8 succeeded at 401 (offset 1 line).
Hunk #9 succeeded at 427 (offset 1 line).
Hunk #10 succeeded at 448 (offset 1 line).
Hunk #11 succeeded at 508 (offset 1 line).
Hunk #12 succeeded at 528 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #2 succeeded at 69 (offset 1 line).
Hunk #3 succeeded at 317 (offset 1 line).
Hunk #4 succeeded at 350 (offset 1 line).
Hunk #5 succeeded at 366 (offset 1 line).
Hunk #6 succeeded at 392 (offset 1 line).
Hunk #7 succeeded at 408 (offset 1 line).
Hunk #8 succeeded at 525 (offset 1 line).
Hunk #9 succeeded at 548 (offset 1 line).
Hunk #10 succeeded at 697 (offset 1 line).
Hunk #11 succeeded at 1061 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
Hunk #2 succeeded at 153 (offset 1 line).
Hunk #3 succeeded at 233 (offset 1 line).
Hunk #4 succeeded at 267 (offset 1 line).
Hunk #5 succeeded at 307 (offset 1 line).
Hunk #6 succeeded at 328 (offset 1 line).
Hunk #7 succeeded at 454 (offset 1 line).
Hunk #8 succeeded at 482 (offset 1 line).
Hunk #9 succeeded at 715 (offset 1 line).
Hunk #10 succeeded at 728 (offset 1 line).
Hunk #11 succeeded at 803 (offset 1 line).
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/usb/usx2y'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/usb'
make[2]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pcmcia'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pcmcia/vx'
make[3]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pcmcia/vx'
make[2]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23/pcmcia'
make[1]: Leaving directory `/home/halfempty/Downloads/alsa-driver-1.0.23'
make -C /lib/modules/2.6.35-24-generic/build SUBDIRS=/home/halfempty/Downloads/alsa-driver-1.0.23  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/halfempty/Downloads/alsa-driver-1.0.23/acore/hwdep.o
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/hwdep.c:1:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/hwdep.c:1:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/halfempty/Downloads/alsa-driver-1.0.23/acore/memory_wrapper.o
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/memory_wrapper.c:1:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/halfempty/Downloads/alsa-driver-1.0.23/acore/memalloc.o
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/memalloc.c:1:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/memalloc.c:1:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/halfempty/Downloads/alsa-driver-1.0.23/acore/sgbuf.o
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/sgbuf.c:1:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm.o
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm.c:1:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm.c:1:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm_native.o
In file included from /home/halfempty/Downloads/alsa-driver-1.0.23/include/config.h:6,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm_native.c:2:
/home/halfempty/Downloads/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
/home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/home/halfempty/Downloads/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/home/halfempty/Downloads/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/home/halfempty/Downloads/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [compile] Error 2

```

Why do I get these errors? How can I fix them?

---

