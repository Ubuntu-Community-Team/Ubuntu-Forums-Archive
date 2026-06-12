---
title: "0ac8:3340 Z-Star Microelectronics Corp. webcam not working"
date: 2011-12-17
forum: General Help
---

### Post by iammak on 2011-12-17
hello all
i am new to the forums. good to see we have a big community here.

i bought a usb webcam so as to click some photos and use it as a decent webcam on ubuntu. the manufacturer says that its plug n play cam but its not working.

lsusb gives "0ac8:3340 Z-Star Microelectronics Corp."

so that means its being detected. 
but when i try to use it with softwares like cheese or skype, i only get a black screen.
the in-built hp webcam is working fine.

also, DMESG command returns this output in the end:

[2097411.304091] usb 1-4: new high speed USB device using ehci_hcd and address 2
[2097411.585975] usb 1-4: configuration #1 chosen from 1 choice
[2097411.588419] uvcvideo: Found UVC 1.00 device Sirius USB2.0 Camera (0ac8:3340)
[2097411.591814] input: Sirius USB2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input25

please help.
i can provide more information if you want.

---

### Post by matt_symes on 2011-12-17
Hi

Not sure i can help here as i don't know much about USB webcams but maybe we can get more information for someone else.

What version of Ubuntu are you using ?

From a terminal type these command and post the results back here.

```
uname -a 
```

```
cat /etc/lsb-release
```

Post the output of

```
lsmod | sort
```

and start cheese from the terminal and post any text output.

```
cheese
```

Kind regards

---

### Post by iammak on 2011-12-18
thanks for the reply

**# uname -a**
Linux makpc 2.6.32-31-generic-pae #61-Ubuntu SMP Fri Apr 8 20:00:13 UTC 2011 i686 GNU/Linux

**# dmesg** (last lines)
[2147042.616595] usb 1-4: new high speed USB device using ehci_hcd and address 5
[2147042.901694] usb 1-4: configuration #1 chosen from 1 choice
[2147042.904207] uvcvideo: Found UVC 1.00 device Sirius USB2.0 Camera (0ac8:3340)
[2147042.907799] input: Sirius USB2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input28


**# cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

**# lsmod | sort**
ac97_bus                1002  1 snd_ac97_codec
agpgart                31788  2 fglrx,intel_agp
ahci                   32232  3 
arc4                    1153  2 
binfmt_misc             6587  1 
bitblit                 4707  1 fbcon
bluetooth              49892  6 hidp,rfcomm,sco,bnep,l2cap,btusb
bnep                    9436  0 
bridge                 45614  0 
btusb                  10957  0 
cfg80211              126528  3 iwlagn,iwlcore,mac80211
coretemp                4417  0 
fat                    47767  1 vfat
fbcon                  35102  72 
fglrx                2093229  29 
font                    7557  1 fbcon
hid                    67096  1 hidp
hidp                   11083  0 
hp_accel               11144  0 
ieee1394               81213  1 ohci1394
input_polldev           2482  1 lis3lv02d
intel_agp              24671  0 
iwlagn                107199  0 
iwlcore               106594  1 iwlagn
jmb38x_ms               7407  0 
joydev                  8740  0 
l2cap                  30624  5 hidp,rfcomm,bnep
led_class               2864  3 iwlcore,hp_accel,sdhci
lirc_dev                8884  1 lirc_ene0100
lirc_ene0100            6600  0 
lis3lv02d               6096  1 hp_accel
lp                      7028  0 
mac80211              205402  2 iwlagn,iwlcore
memstick                8237  1 jmb38x_ms
mii                     4381  1 r8169
Module                  Size  Used by
nls_cp437               4919  1 
nls_iso8859_1           3249  1 
ohci1394               27238  0 
output                  1871  1 video
parport                32635  2 ppdev,lp
ppdev                   5259  0 
psmouse                63245  0 
r8169                  34364  0 
rfcomm                 33421  0 
sco                     7885  0 
sdhci                  15654  1 sdhci_pci
sdhci_pci               5502  0 
serio_raw               3978  0 
snd                    56719  22 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_ac97_codec        100728  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
snd_atiixp_modem        9087  0 
snd_hda_codec          87096  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_atihdmi     2399  1 
snd_hda_codec_idt      54083  1 
snd_hda_intel          20959  2 
snd_hwdep               5668  1 snd_hda_codec
snd_intel8x0m          10782  0 
snd_mixer_oss          13961  1 snd_pcm_oss
snd_page_alloc          7236  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
snd_pcm                71934  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_pcm_oss            34603  0 
snd_rawmidi            19141  1 snd_seq_midi
snd_seq                48106  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_dummy           1498  0 
snd_seq_midi            4621  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq_oss            27658  0 
snd_timer              18710  2 snd_pcm,snd_seq
snd_via82xx_modem       8576  0 
softcursor              1189  1 bitblit
soundcore               6620  1 snd
stp                     1655  1 bridge
tileblit                2031  1 fbcon
uvcvideo               57342  0 
v4l1_compat            13251  2 uvcvideo,videodev
vboxdrv               169169  2 vboxnetadp,vboxnetflt
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vfat                    8933  1 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
video                  17375  0 
videodev               34361  1 uvcvideo

---

### Post by matt_symes on 2011-12-18
Hi

And what output do you get if you start cheese from the command line ?

Kind regards

---

### Post by iammak on 2011-12-18
hi
no output of any kind when in start cheese in cmd line
in options i can choose the cam as sirius cam. but black screen only
regards

---

### Post by matt_symes on 2011-12-18
Hi

I think you may need the gspca driver and not the uvcvideo driver for this camera.

Try this. Open a terminal and type

```
sudo modprobe -r uvcvideo
```

Enter your password. It will not be echoed to the screen. Then type

```
sudo modprobe gspca
```

This should load the new driver. Then start cheese from the command line.

```
cheese
```

Post back results.

As i said, i am no expert with webcams so i am hoping someone with more experience will chime in.

Kind regards

---

