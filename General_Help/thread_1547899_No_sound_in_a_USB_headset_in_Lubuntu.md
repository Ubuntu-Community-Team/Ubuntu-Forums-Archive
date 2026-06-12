---
title: "No sound in a USB headset in Lubuntu"
date: 2010-08-07
forum: General Help
---

### Post by HotForLinux on 2010-08-07
I want to install Lubuntu in an old  PC-Box.
I have booted from the Live-CD but I can hear no sound through the USB headset that needs to be installed.

I'll try to give all the information that, according to what I have read, might be relevant so that I don't need to boot again from this PC and Live-CD. If there's irrelevant info, just tell me and I'll delete it to reduce the post's length.

```

**$ uname -a**
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.


**$ head -1 /proc/asound/card0/codec97#0/ac97#0-0***
==> /proc/asound/card0/codec97#0/ac97#0-0 <==
0-0/0: Analog Devices AD1885

==> /proc/asound/card0/codec97#0/ac97#0-0+regs <==
0:00 = 0410

**$ ls /proc/asound/card1/**
id  midi0  oss_mixer

**$ ls /proc/asound/card2/**
id  oss_mixer  pcm0c  pcm0p  stream0  usbbus  usbid

``````
**$ sudo lshw -short**
sudo lshw -short
H/W path           Device       Class       Description
=======================================================
                                system      Computer
/0                              bus         D815EEA
/0/0                            memory      64KiB BIOS
/0/4                            processor   Celeron (Coppermine)
/0/4/5                          memory      32KiB L1 cache
/0/4/6                          memory      128KiB L2 cache
/0/2f                           memory      512MiB System Memory
/0/2f/0                         memory      512MiB DIMM DRAM Synchronous 100 MHz (10.0 
/0/2f/1                         memory      [empty]
/0/2f/2                         memory      [empty]
/0/100                          bridge      82815 815 Chipset Host Bridge and Memory Co
/0/100/2                        display     82815 Chipset Graphics Controller (CGC)
/0/100/1e                       bridge      82801 PCI Bridge
/0/100/1e/8        eth0         network     82801BA/BAM/CA/CAM Ethernet Controller
/0/100/1f                       bridge      82801BA ISA Bridge (LPC)
/0/100/1f.1        scsi0        storage     82801BA IDE U100 Controller
/0/100/1f.1/0      /dev/sda     disk        20GB ST320410A
/0/100/1f.1/0/1    /dev/sda1    volume      6000MiB Windows NTFS volume
/0/100/1f.1/0/2    /dev/sda2    volume      486MiB Linux swap volume
/0/100/1f.1/0/3    /dev/sda3    volume      12GiB EXT3 volume
/0/100/1f.1/1      /dev/cdrom   disk        DVD-ROM GDR8161B
/0/100/1f.1/1/0    /dev/cdrom   disk        
/0/100/1f.1/0.1.0  /dev/cdrom1  disk        SCSI CD-ROM
/0/100/1f.2                     bus         82801BA/BAM USB Controller #1
/0/100/1f.3                     bus         82801BA/BAM SMBus Controller
/0/100/1f.4                     bus         82801BA/BAM USB Controller #1
/0/100/1f.5                     multimedia  82801BA/BAM AC'97 Audio Controller

``````
**$ cat /etc/modprobe.d/alsa-base.conf**
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

```I have executed **alsamixer**, chosen "Logitech USB Headset" and raised its speaker level but still can't hear an ogg file saved in the desktop with aqualung, for instance.

---

### Post by cavalier911 on 2010-08-07
Determine the device name to use as the output option in the program which will be playing the soundfile.
```
[SIZE=1]rj@lubuntu:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=YMF740
    Yamaha DS-1L (YMF740), YMFPCI
    Default Audio Device
front:CARD=YMF740,DEV=0
    Yamaha DS-1L (YMF740), YMFPCI
    Front speakers
rear:CARD=YMF740,DEV=0
    Yamaha DS-1L (YMF740), YMFPCI - Rear PCM
    Rear speakers
surround40:CARD=YMF740,DEV=0
    Yamaha DS-1L (YMF740), YMFPCI
    4.0 Surround output to Front and Rear speakers
iec958:CARD=YMF740,DEV=0
    Yamaha DS-1L (YMF740), YMFPCI - IEC958
    IEC958 (S/PDIF) Digital Audio Output
[/SIZE] [SIZE=1][COLOR=Red]default:CARD=Headset[/COLOR][/SIZE][SIZE=1]
    Logitech USB Headset, USB Audio
    Default Audio Device
front:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
[/SIZE]
```Play a wav file with aplay through my headphones.
```
aplay -D default:CARD=Headset song.wav
```Play music with aqualung through my headphones.
```
aqualung -o alsa -d default:CARD=Headset
```Set alsamixer device with F6 choose 1Logitech USB Headset to control volume
Volume control in lxpanel doesn't work for headphones

Make a menu entry for launching aqualung that outputs to headphones:
Copy/rename /usr/share/applications/aqualung.desktop
```
sudo cp /usr/share/applications/aqualung.desktop /usr/share/applications/aquahead.desktop
``````
sudo nano /usr/share/applications/aquahead.desktop
``````
[Desktop Entry]
Name=**Aquahead**
Comment=Gapless audio player
Exec=aqualung **-o alsa -d default:CARD=Headset**
Icon=aqualung.xpm
Categories=GTK;AudioVideo;Audio;Player;
Terminal=false
Type=Application
Encoding=UTF-8
```

---

### Post by HotForLinux on 2010-08-08
Thank you, cavalier911.
That was clear and useful. Although I do not understand those ***aplay*** outputs, it worked fine. The only problem I see is doing that for every sound application, not only in my personal case but in an imaginary complex installation. I mentioned Aqualung as an example, but the sound applications I really need to use in this box are: Skype /with the microphone also), Chromium web browser and Firefox (with flash plugin). 

Do you know if there's a simple way to make the hadphones the default sound card or
permanently asign the headset to an application or
make the headset the default card when it is connected,...?

In this thread they talk about a solution to this problem for Ubuntu, but I don't know what steps should I follow and whether I can do it in Lubuntu:
[http://ubuntuforums.org/showthread.php?t=1533698](http://ubuntuforums.org/showthread.php?t=1533698)

Do you have any idea?

---

### Post by HotForLinux on 2010-08-10
*bump*

---

### Post by HotForLinux on 2010-11-22
* = bump = *

---

