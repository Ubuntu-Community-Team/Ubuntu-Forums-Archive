---
title: "Asrock ION 330 No sound with HDMI to TV, Help!! Ubuntu 9.10"
date: 2010-01-01
forum: General Help
---

### Post by tliljeqvist on 2010-01-01
Hi folks,

trying to put up my HTPC with Ubuntu 9.10 but I cant get any sound to work. Im using a HDMI cable between the pc and TV. Computer is an Asrock ION HT/BD 330. Also running a 64 bit version of Ubuntu.

I have upgraded all I know or think I know what to do but still with no luck.

I asume you need some basic info to help out so I try my best to give you what you need to help out.

To start of heres my multimeda.

*-multimedia            
       description: Audio device
       product: MCP79 High Definition Audio
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: b1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:23 memory:fae78000-fae7bfff

my cat /proc/asound/version is as follow
Advanced Linux Sound Architecture Driver Version 1.0.22.
Compiled on Dec 17 2009 for kernel 2.6.31-16-generic (SMP).

my lsmod is as follow.

Module                  Size  Used by
vfat                   13184  0 
fat                    59832  1 vfat
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_nvhdmi     6304  1 
snd_hda_codec_realtek   288292  1 
snd_hda_intel          30208  0 
snd_hda_codec          96384  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9448  1 snd_hda_codec
snd_pcm_oss            44320  0 
snd_mixer_oss          19040  1 snd_pcm_oss
snd_pcm                93672  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3588  0 
snd_seq_oss            33696  0 
snd_seq_midi            8320  0 
snd_rawmidi            27200  1 snd_seq_midi
snd_seq_midi_event      8544  2 snd_seq_oss,snd_seq_midi
snd_seq                61216  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    2144  2 
ecb                     3296  2 
snd_timer              25872  2 snd_pcm,snd_seq
ath9k                 278176  0 
snd_seq_device          8532  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              209912  1 ath9k
led_class               5256  1 ath9k
ath                    10304  1 ath9k
snd                    78088  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
nvidia              10316904  40 
psmouse                57124  0 
soundcore               9088  1 snd
snd_page_alloc         11088  2 snd_hda_intel,snd_pcm
serio_raw               6596  0 
joydev                 13088  0 
shpchp                 37756  0 
cfg80211              109144  3 ath9k,mac80211,ath
i2c_nforce2             8168  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
hid_logitech           10112  0 
ff_memless              6504  1 hid_logitech
usbhid                 43968  1 hid_logitech
usb_storage            65984  0 
forcedeth              61292  0 

My modinfo soundcore is as follow
filename:       /lib/modules/2.6.31-16-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-16-generic SMP mod_unload modversions


Any help is appreciated and I have tried to see if its still muted but dunno....

rgds,

Thomas

---

### Post by perevera on 2010-01-01
I'm having the exact same problem.

I think I'm gonna try to upgrade ALSA as explained in:

[http://ubuntuforums.org/showthread.php?t=1046137&highlight=ASRock+ION](http://ubuntuforums.org/showthread.php?t=1046137&highlight=ASRock+ION)

I'll let you know the result...

---

### Post by tliljeqvist on 2010-01-03
Hi,

just wanted to update this as i got it to work. I just downloaded and installed the gnome alsa mixer, unmuted everything and clicked in the ice9.... something and wola worked.

Thanks though and best of luck.

rgds,

Thomas

---

### Post by perevera on 2010-01-07
> **tliljeqvist said:**
> Hi,

just wanted to update this as i got it to work. I just downloaded and installed the gnome alsa mixer, unmuted everything and clicked in the ice9.... something and wola worked.

Thanks though and best of luck.

rgds,

Thomas

Thanks, Thomas, but I am having no luck.

I installed ALSA version 1.0.22.1, but with 'alsamixer' I cannot find a track like 'HDMI' or not even 'IEC958' (which I believe corresponds to S/PDIF output) to unmute them.

Neither gnome-alsamixer does the trick.

In summary, I still don't have sound at the HDMI output, although I have sound at the analog stereo output ('front').

Some info about my system:

perevera@minipc:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

perevera@minipc:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: ALC889A Analog [ALC889A Analog]
Subdispositivos: 1/1
Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 1: ALC889A Digital [ALC889A Digital]
Subdispositivos: 1/1
Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 3: NVIDIA HDMI [NVIDIA HDMI]
Subdispositivos: 1/1
Subdispositivo #0: subdevice #0
perevera@minipc:~$ aplay -L
null
Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
HDA NVidia, ALC889A Analog
Default Audio Device
front:CARD=NVidia,DEV=0
HDA NVidia, ALC889A Analog
Front speakers
surround40:CARD=NVidia,DEV=0
HDA NVidia, ALC889A Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
HDA NVidia, ALC889A Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
HDA NVidia, ALC889A Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
HDA NVidia, ALC889A Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
HDA NVidia, ALC889A Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
HDA NVidia, ALC889A Digital
IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
HDA NVidia, NVIDIA HDMI
HDMI Audio Output

---

### Post by postadelmaga on 2010-01-20
[Here ]("http://ptspts.blogspot.com/2009/08/asrock-ion-330-nettop-with-jaunty.html") a solution for that problem.


> 
HDMI and S/PDIF audio output
When diagnosing sound problems, make sure that pulseaudio is not running:

sudo killall pulseaudio

Please also make sure that no other program might be using the soundcard: disable system sounds, kill all web browsers (to kill the flash player), and kill all media players.

To get default audio output on the analog stereo jack, run

$ mplayer -ao alsa $FILE

To force audio output on the analog stereo jack, run

$ mplayer -ao alsa:device=front=NVidia $FILE

To force audio output on HDMI, run

$ mplayer -ao alsa:device=hdmi=NVidia $FILE

To force output on S/PDIF, run

$ mplayer -ao alsa:device=iec958=NVidia $FILE

To list all available audio output devices, run

$ aplay -L

Please note than when specifying anything other than -ao alsa to MPlayer, you may lose DMIX support, so you won't be able to run two playbacks at the same time, and MPlayer would print:

[AO_ALSA] Unable to set hw-parameters: Device or resource busy

It is possible to fix that by using plain -ao alsa and specifying the the output device in $HOME/.asourdrc. Using the environment variable ALSA_CARD does work, but ALSA_PCM_DEVICE doesn't seem to work. Set up your $HOME/.asoundrc like this:

defaults.pcm.!card NVidia
defaults.ctl.!card NVidia
defaults.pcm.!device 0
defaults.ctl.!device 0

The device number 0 is analog output, 1 is S/PDIF and 3 is HDMI. The device numbers come from the output of aplay -l. 


---

### Post by gesquive on 2010-03-17
> **tliljeqvist said:**
> Hi,

just wanted to update this as i got it to work. I just downloaded and installed the gnome alsa mixer, unmuted everything and clicked in the ice9.... something and wola worked.

Thanks though and best of luck.

rgds,

Thomas

Tom,

Amazing insight, I installed the gnome-alsamixer package, ran it and IEC958 output was unchecked, the moment that i checked it all of my sound output instantly worked! Thanks a ton.

---

### Post by perevera on 2010-04-03
> **gesquive said:**
> Tom,

Amazing insight, I installed the gnome-alsamixer package, ran it and IEC958 output was unchecked, the moment that i checked it all of my sound output instantly worked! Thanks a ton.

This does not work for me.

I have all IEC958 options checked but the sound does not work on the HDMI output.

I am using the analog output, which corresponds to the Front bar.

Does anyone has some idea on how to debug this problem?

---

### Post by postadelmaga on 2011-02-23
**First of all:**
Unmute **"S/SDIF 1"** control ( open **alsamixer** and do it )

... Then
**to test audio:**
```
mplayer -ao alsa:device=hdmi=NVidia http://www.wdav.org/streams/WDAV-128k.m3u
```
That could you confirm that audio works and you need only to config Pulseaudio output 
... if so ...

**On Ubuntu**: right click volume and configure output ... **you should be ok now**


**On Kubuntu**: I had to install **pavucontrol** and run output to configure it ...
of course:
```
sudo aptitude install pavucontrol
``` 

**nothing else to modify ( no asound.conf or whatever )**

---

