---
title: "Sound problemS"
date: 2006-05-18
forum: General Help
---

### Post by titou on 2006-05-18
Hello,

I have different questions about sound issues I didn't find answer on this forum : 
My PC : 
AMD XP 2600+
MB MSI KT333
1 G DDR
Maxtro 250
GeForce 6600 GT
Sound Blaster Audigy
 - Kubuntu Dapper

1 - I have a Logitech itouch elite keyboard, the media keys work fine except for XF86RaiseVolume, strangely it is detected when I want to assign it but it doesn't work... (Lower volume work) any idea ?

2 - My sound blaster Audigy Wroks fine with ALSA but I have 2 other sound card I can't make work, one is a usb headset (Kobishi)  and the other is an integrated VIA VT8233/A/8235/8237 AC97 Audio Controller. I would like to use one of the two secondary sound card for skype and VoIP related software but I can't make them work. I know skype uses OSS and I read all about making it work with the alsa-oss layer but it doesn't help me ... 

So is it possible to launch artsdsp choosing a sound card or install oss for a secondary card only or else sonething I didn't tink about ? 

I'll keep trying waiting for answers ](*,)

---

### Post by DeusEx on 2006-05-18
your problem is probably the numbers the soundcards get.

There are some older posts regarding the multiple soundcards problem.

If I recall correctly, you should set the numbers of the soundcards in alsa-base.conf


About the skype problem: it can use a secondairy oss soundcard, but you must use the hijack script. Works like a charm for me. see here: [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

---

### Post by titou on 2006-05-19
After couple of tests, I found out that the integrated soundcard doesn't work (I never used it before) so I tryed to install my usb headset.

#lsusb 
Bus 001 Device 003: ID 06e6:7210 Tiger Jet Network, Inc.

I don't understand some stuffs about ALSA config, I red on the forum I have to modify some alsa-base.conf or other files like asound.conf wich I cannot find on my box !! 

When I test the usb sound card with alsaplayer, i get this : 

#alsaplayer -d hw:1

error on set_channels (2)
Unavailable hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 8000
PERIOD_TIME: [4000 32768000]
PERIOD_SIZE: [32 262144]
PERIOD_BYTES: [64 524288]
PERIODS: [2 1024]
BUFFER_TIME: [8000 65536000]
BUFFER_SIZE: [64 524288]
BUFFER_BYTES: [128 1048576]
TICK_TIME: 1000
error on set_channels (2)
Unavailable hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 8000
PERIOD_TIME: [4000 32768000]
PERIOD_SIZE: [32 262144]
PERIOD_BYTES: [64 524288]
PERIODS: [2 1024]
BUFFER_TIME: [8000 65536000]
BUFFER_SIZE: [64 524288]
BUFFER_BYTES: [128 1048576]
TICK_TIME: 1000
failed to configure output device...trying OSS
error on set_channels (2)
Unavailable hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 8000
PERIOD_TIME: [4000 32768000]
PERIOD_SIZE: [32 262144]
PERIOD_BYTES: [64 524288]
PERIODS: [2 1024]
BUFFER_TIME: [8000 65536000]
BUFFER_SIZE: [64 524288]
BUFFER_BYTES: [128 1048576]
TICK_TIME: 1000
error on set_channels (2)
Unavailable hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 8000
PERIOD_TIME: [4000 32768000]
PERIOD_SIZE: [32 262144]
PERIOD_BYTES: [64 524288]
PERIODS: [2 1024]
BUFFER_TIME: [8000 65536000]
BUFFER_SIZE: [64 524288]
BUFFER_BYTES: [128 1048576]
TICK_TIME: 1000
failed to configure output device...trying OSS

if I want to get to the alsamixer, I get this : 
#alsamixer -c 1

alsamixer: function snd_mixer_load failed: Invalid argument

I found somepost about a guy having the same output but not the same problem, I actually get sound when I do this : 

#aplay -D plughw:1 somefile.wav

I supposed I have to define my secondary sound card somewhere but I don't know how and where !? 

anyone ?

and for the keyboard issue, anyone knows why I can't get it to raise volume ?

---

### Post by DeusEx on 2006-05-29
I 'm not on my linux box right now, but i'll check asap.

still having the problem?

---

### Post by titou on 2006-05-29
yes, actually, my audigy works more than fine except that sometimes, the sound cards switches at boot so I get the sound on my USB headset, I then have to rebbot with the headset unpluged. 

I would like to know how to install and configure my headset so I could use it correctly with Skype And Wengophone ...

and I still have that RaiseVolume key not working ...

---

### Post by DeusEx on 2006-05-29
for the volume thing you could try upgrading to dapper

here's my /etc/modprobe.d/alsa-base:
(note the last 4 lines)
```

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7
# Load optional modules above their base modules
install snd modprobe --ignore-install snd && { modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-install snd-via82xx ; modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a modprobe --ignore-install snd-ad1816a && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 modprobe --ignore-install snd-ad1848 && /lib/alsa/modprobe-post-install snd-ad1848
install snd-ali5451 modprobe --ignore-install snd-ali5451 && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 modprobe --ignore-install snd-als100 && /lib/alsa/modprobe-post-install snd-als100
install snd-als4000 modprobe --ignore-install snd-als4000 && /lib/alsa/modprobe-post-install snd-als4000
install snd-armaaci modprobe --ignore-install snd-armaaci && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi modprobe --ignore-install snd-asihpi && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp modprobe --ignore-install snd-atiixp && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 modprobe --ignore-install snd-au1x00 && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 modprobe --ignore-install snd-au8810 && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 modprobe --ignore-install snd-au8820 && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 modprobe --ignore-install snd-au8830 && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 modprobe --ignore-install snd-azt2320 && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 modprobe --ignore-install snd-azt3328 && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 modprobe --ignore-install snd-ca0106 && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 modprobe --ignore-install snd-cmi8330 && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmipci modprobe --ignore-install snd-cmipci && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 modprobe --ignore-install snd-cs4231 && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 modprobe --ignore-install snd-cs4232 && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 modprobe --ignore-install snd-cs4236 && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 modprobe --ignore-install snd-cs4281 && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx modprobe --ignore-install snd-cs46xx && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-darla20 modprobe --ignore-install snd-darla20 && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 modprobe --ignore-install snd-darla24 && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x modprobe --ignore-install snd-dt019x && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g modprobe --ignore-install snd-echo3g && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x modprobe --ignore-install snd-emu10k1x && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 modprobe --ignore-install snd-ens1370 && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 modprobe --ignore-install snd-ens1371 && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 modprobe --ignore-install snd-es1688 && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx modprobe --ignore-install snd-es18xx && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 modprobe --ignore-install snd-es1938 && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 modprobe --ignore-install snd-es1968 && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 modprobe --ignore-install snd-es968 && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 modprobe --ignore-install snd-fm801 && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x modprobe --ignore-install snd-fm801-tea575x && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 modprobe --ignore-install snd-gina20 && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 modprobe --ignore-install snd-gina24 && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic modprobe --ignore-install snd-gusclassic && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme modprobe --ignore-install snd-gusextreme && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax modprobe --ignore-install snd-gusmax && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony modprobe --ignore-install snd-harmony && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel modprobe --ignore-install snd-hda-intel && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp modprobe --ignore-install snd-hdsp && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm modprobe --ignore-install snd-hdspm && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 modprobe --ignore-install snd-ice1712 && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 modprobe --ignore-install snd-ice1724 && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo modprobe --ignore-install snd-indigo && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj modprobe --ignore-install snd-indigodj && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio modprobe --ignore-install snd-indigoio && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 modprobe --ignore-install snd-intel8x0 && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave modprobe --ignore-install snd-interwave && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb modprobe --ignore-install snd-interwave-stb && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 modprobe --ignore-install snd-korg1212 && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 modprobe --ignore-install snd-layla20 && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 modprobe --ignore-install snd-layla24 && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 modprobe --ignore-install snd-maestro3 && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia modprobe --ignore-install snd-mia && /lib/alsa/modprobe-post-install snd-mia
install snd-miro modprobe --ignore-install snd-miro && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart modprobe --ignore-install snd-mixart && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona modprobe --ignore-install snd-mona && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 modprobe --ignore-install snd-mpu401 && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle modprobe --ignore-install snd-msnd-pinnacle && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav modprobe --ignore-install snd-mtpav && /lib/alsa/modprobe-post-install snd-mtpav
install snd-nm256 modprobe --ignore-install snd-nm256 && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 modprobe --ignore-install snd-opti92x-ad1848 && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 modprobe --ignore-install snd-opti92x-cs4231 && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x modprobe --ignore-install snd-opti93x && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 modprobe --ignore-install snd-pc98-cs4232 && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp modprobe --ignore-install snd-pcsp && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr modprobe --ignore-install snd-pcxhr && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf modprobe --ignore-install snd-pdaudiocf && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus modprobe --ignore-install snd-pdplus && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 modprobe --ignore-install snd-portman2x4 && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac modprobe --ignore-install snd-powermac && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 modprobe --ignore-install snd-pxa2xx-ac97 && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-rme32 modprobe --ignore-install snd-rme32 && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 modprobe --ignore-install snd-rme96 && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 modprobe --ignore-install snd-rme9652 && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 modprobe --ignore-install snd-s3c2410 && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 modprobe --ignore-install snd-sa11xx-uda1341 && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 modprobe --ignore-install snd-sb16 && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 modprobe --ignore-install snd-sb8 && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe modprobe --ignore-install snd-sbawe && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serialmidi modprobe --ignore-install snd-serialmidi && /lib/alsa/modprobe-post-install snd-serialmidi
install snd-serial-u16550 modprobe --ignore-install snd-serial-u16550 && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy modprobe --ignore-install snd-sgalaxy && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes modprobe --ignore-install snd-sonicvibes && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape modprobe --ignore-install snd-sscape && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 modprobe --ignore-install snd-sun-amd7930 && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 modprobe --ignore-install snd-sun-cs4231 && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri modprobe --ignore-install snd-sun-dbri && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident modprobe --ignore-install snd-trident && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio modprobe --ignore-install snd-usb-audio && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y modprobe --ignore-install snd-usb-usx2y && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 modprobe --ignore-install snd-vx222 && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxp440 modprobe --ignore-install snd-vxp440 && /lib/alsa/modprobe-post-install snd-vxp440
install snd-vxpocket modprobe --ignore-install snd-vxpocket && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront modprobe --ignore-install snd-wavefront && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci modprobe --ignore-install snd-ymfpci && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# 1e kaart: SBLive 5.1 [SB0060]
options snd-emu10k1 index=0
# 2e kaart: Ensoniq AudioPCI 
options snd-ens1371 index=1

```

you should set the usb card to index=1 and the audigy to index=0.

for skype go here: [http://195.38.3.142:6502/skype/](http://195.38.3.142:6502/skype/)

good luck!

---

### Post by titou on 2006-06-08
hey,

thanks, adding those lines (device 0 and 1) worked, now soundcards don't swap anymore, I also find out how to correctly use my usb device.

It actually looks like it only work on oss. So my soundbalster works on XALSA and I activated artS on /dev/dsp1 with OSS so I can use multiple softwares on my headset. I added this : 

[CODE]   MultiDriver=true [CODE]

in the Global config of  " ~/.kde/share/config/kmixrc " so it can use ALSA & OSS together.

It works fine but I still have a small problem :

The sound I get is perfect but poeple don't hear me very well. Sound is very low   even thought it's set to maximum in Kmix. Anybody knows how I can improve the sound quality of the microphone ? (Kmix doesn't have Mic Boost for the headset usb device)

---

### Post by aoberoi on 2006-06-10
I'm having a similar keyboard problem. I tried setting the keyboard shortcuts in the preferences menu myself. The Volume Down will work but the Volume Down doesnt. Also, the Next, Prev, Play, and Stop buttons dont do anything. That may be because of my media player (Rhythmbox) but I'm not sure. I remember when i had breezy all the buttons worked fine, i just tried customizing the buttons myself (probably shouldn't have done that). Does anyone have any suggestions on how to fix this?

---

### Post by DeusEx on 2006-06-22
just saw this is the BB 5.10 support forum :)

dapper drake fixed the quick-button problems for me.

---

