---
title: "ubuntu 10.04 microphone not working"
date: 2011-10-12
forum: General Help
---

### Post by sayem.bd on 2011-10-12
Hi, I am new to ubuntu and installed it in my desktop PC just a few days ago. Everything in my PC is working fine except the microphone. I couldn't get it to work. I have searched the net and tried to apply several ways which others claim to be the solution - 

    1. I opened the Sound Preferences, switched to the Input tab and made sure that the Input volume isn't muted.
    
    2. I've installed alsamixer and set Master, PCM and Capture volume to 100

    3. I have installed Default Sound Card from the Ubuntu Software Center, then installed Pulseaudio Volume Control. Then I opened the volume control and switched to the input device tab. Then I tried various sound level combination of Front left and Front right volume control. I also made sure that the mute button there is also not selected.

    4. I have opened the alsa-base.conf file from /etc/modprobe.d/alsa-base.conf and added this line at the end - options snd-hda-intel position_fix=1 , but still my microphone doesn't work.

Here's some info about my config - 

```
    cat /proc/asound/cards
        0 [Intel          ]: HDA-Intel - HDA Intel
                             HDA Intel at 0xfdff8000 irq 16
```

```
dpkg -l | grep "alsa"
    ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
    ii  alsa-firmware-loaders                     1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
    ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
    ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
    ii  gnome-alsamixer                           0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
    ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
```


    ```
lsmode
        Module                  Size  Used by
        fbcon                  35102  71 
        tileblit                1999  1 fbcon
        font                    7557  1 fbcon
        bitblit                 4707  1 fbcon
        softcursor              1189  1 bitblit
        vga16fb                11385  0 
        vgastate                8961  1 vga16fb
        binfmt_misc             6587  1 
        snd_hda_codec_via      27111  0 
        i915                  288963  3 
        snd_hda_intel          22069  6 
        snd_hda_codec          74201  2 snd_hda_codec_via,snd_hda_intel
        snd_hwdep               5412  1 snd_hda_codec
        snd_pcm_oss            35308  0 
        snd_mixer_oss          13746  1 snd_pcm_oss
        snd_pcm                70694  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
        snd_seq_dummy           1338  0 
        snd_seq_oss            26722  0 
        snd_seq_midi            4557  0 
        snd_rawmidi            19056  1 snd_seq_midi
        snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
        snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
        snd_timer              19098  2 snd_pcm,snd_seq
        snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
        ppdev                   5259  0 
        drm_kms_helper         29329  1 i915
        parport_pc             25962  1 
        atl1e                  59778  0 
        snd                    54244  21 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss, nd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
        drm                   163651  4 i915,drm_kms_helper
        i2c_algo_bit            5028  1 i915
        video                  17375  1 i915
        output                  1871  1 video
        psmouse                63677  0 
        serio_raw               3978  0 
        intel_agp              24375  2 i915
        agpgart                31724  2 drm,intel_agp
        soundcore               6620  1 snd
        snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
        lp                      7028  0 
        parport                32635  3 ppdev,parport_pc,lp
        floppy                 53016  0 
```

and this is my /etc/modprobe.d/alsa-base.conf - 

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel position_fix=1
```

This is my linux info - 

```
    uname -a
                Linux sayem-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
```

```
    lsb_release -a
        No LSB modules are available.
        Distributor ID:	Ubuntu
        Description:	Ubuntu 10.04.2 LTS
        Release:	10.04
        Codename:	lucid
```


I really don't have a clue what to do........ ](*,)](*,)

---

### Post by kdavh on 2011-10-17
My internal microphone is not working as well.  I am using a Lenovo 3000 v200 laptop.  It worked fine with Natty 11.04, but since doing a clean install of 11.10, it no longer works.  I've tried all the steps that sayem.bd tried

---

