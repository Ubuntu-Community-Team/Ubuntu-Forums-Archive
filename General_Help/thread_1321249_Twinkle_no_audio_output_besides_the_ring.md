---
title: "Twinkle: no audio output besides the ring"
date: 2009-11-09
forum: General Help
---

### Post by mike_11 on 2009-11-09
Problem description: 
Trying to use Twinkle for pc-to-pc calls. I type in an sip number then hear the ring sound.
Twinkle then prints: `Line 1: far end answered call.' but there is no audio output (I've tried several SIP numbers).
Sounds works perfect with other applications (vlc, epiphany etc.).

Details on my system:
Linux: Debian Lenny Linux version 2.6.26-1-686 (Debian 2.6.26-8)

My sip account is with ekiga.net

hardware:
lspci|grep Audio: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

aplay -L
default:CARD=Intel
    HDA Intel, ALC262 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC262 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

cat /etc/esound/esd.conf:
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

lsmod|grep snd:
snd_hda_intel         324248  1 
snd_pcm_oss            32800  0 
snd_mixer_oss          12320  1 snd_pcm_oss
snd_pcm                62628  2 snd_hda_intel,snd_pcm_oss
snd_timer              17800  1 snd_pcm
snd                    45604  7 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               6368  1 snd
snd_page_alloc          7816  2 snd_hda_intel,snd_pcm


What I've done:
-installed twinkle 1.4.2 form the Ubuntu rep.: [http://ubuntuforums.org/archive/inde...t-1211615.html]("http://ubuntuforums.org/archive/index.php/t-1211615.html")
-disabled flash plugin in epiphany:  [http://blog.foppiano.org/2009/07/12/...uration-howto/]("http://blog.foppiano.org/2009/07/12/twinkle-configuration-howto/")
-checked (with alsamixer) that both front mic and mic are enabled:  [http://blog.foppiano.org/2009/07/12/...uration-howto/]("http://blog.foppiano.org/2009/07/12/twinkle-configuration-howto/")
-set in /etc/esound/esd.conf: auto_spawn=1
-set in Twinkle :
        Ring tone: ALSA: plughw: 0,0 HDA Intel (ALC262 Analog)
        Speaker: ALSA: plughw: 0,0 HDA Intel (ALC262 Analog)
        Microphone: ALSA: plughw: 0,0 HDA Intel (ALC262 Analog)
-system->preferneces->soound->sounds->ticked `Enable software sound mixing (ESD)'

Alas, it still produce any audio output besides the intial ring. Any suggestions?

Cheers,
Mike.

---

