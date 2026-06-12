---
title: "Still have no sound"
date: 2010-06-13
forum: General Help
---

### Post by hxcfelony on 2010-06-13
OK! I have had this problem for far too long, my onboard sound will not  work, i went from Xubuntu, to Vista now to here! NO the mute is not on,  it says i have sound but I dont! I did the lspci command and got this:
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset  Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire  II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID  Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc.  VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1  Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1  Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1  Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1  Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge  [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc.  VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem  Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II]  (rev 7:cool:
01:00.0 VGA compatible controller: VIA Technologies, Inc.  KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
ALSO I have a custom built computer that came with a Rocket Fish sound  card model RF-51SDCD that I rip out (no known drivers for that sound  card). I have a Compaq Presario 061. Model number is DT076A-ABA S6200CL  NA410. My motherboard is an ASUSTek Kamet2. The firmeware is Phoenix  Technologies version 3.05 (cant find an update for that either).
Well I hope the Ubuntu community can help because this is the last straw  for me, I never had any trouble like this and this is very frustrating.
Good Luck!

---

### Post by issachan on 2010-06-13
While I don't understand all that code type stuff you posted, I think it could be a number of things, the sound card, the speakers, the settings in the os, and possibly some volume setting. I know in the past I would have sound then out of nowhere it would stop, but if I restarted the computer it came back - still no idea what caused it. Anyway try the most simple solutions first, check any volume settings in the os. Since it acknowledges sound on some level it seems like the sound card is working, so check the speakers themselves. Are they damaged, etc. Then the next thing I'd check is installing a sound card and change your os settings to work with it and see if that does the trick.

Anyway, hope this helps, good luck!

---

### Post by hxcfelony on 2010-06-13
Ya I know what you mean but i try everything. I used other speakers, I pulled the sound card out and see if the onboard works which it does not, then I installed Ubuntu recently and that did not help. Now i am on my last leg here and its annoying i cant communicate with ppl like i use too :(

---

### Post by lidex on 2010-06-13
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by hxcfelony on 2010-06-13
uname -a=Linux evanpwn-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
aplay -l=**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
head -1 /proc/asound/card0/codec97#0/ac97#0-0 = 0-0/0: Realtek ALC658D

---

### Post by hxcfelony on 2010-06-13
dpkg -l | grep "alsa"= ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

---

### Post by lidex on 2010-06-13
I don't see alsa-oss in there - you should install that. While you're at it install gnome-alsamixer. That is a gui frontend for alsamixer.
```
sudo apt-get install alsa-oss gnome-alsamixer
```
Next follow the alsa-upgrade link in my sig to get v 1.0.23

---

### Post by lidex on 2010-06-13
According to alsa documentation, your sound chip should be using this module:
```
snd-via82xx
```
Your output shows:
```
Realtek ALC658D 
```
which I have not seen. What is the output of this command:
```
lsmod | grep snd
```
Try loading that module:
```
sudo modprobe snd-via82xx
```

---

### Post by JimGvo on 2010-07-25
I'm not the original owner of the problem, but it sounds like I have the same problem.  The system was working properly when I was running Hardy, but and upgrade to 10.04 has left me with no sound.  One thing different is that I also show no speaker icon and the "add to panel" doesn't show one either.  


> ]0;jim@blackie: /home/jimjim@blackie:~$ uname -a
Linux blackie 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
]0;jim@blackie: /home/jimjim@blackie:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
]0;jim@blackie: /home/jimjim@blackie:~$ dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.22.1+dfsg-0ubuntu3                                     ALSA driver configuration files
ii  alsa-oss                                   1.0.17-3                                                   ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.22-0ubuntu5                                            ALSA utilities
ii  bluez-alsa                                 4.60-0ubuntu8                                              Bluetooth audio support
ii  gnome-alsamixer                            0.9.7~cvs.20060916.ds.1-2                                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                         0.10.28-1                                                  GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-6ubuntu1                                            Enlightened Sound Daemon (ALSA) - transitional package
ii  libpt-1.10.10-plugins-alsa                 1.10.10-3ubuntu1                                           Portable Windows Library Audio Plugin for the ALSA Inte
rc  libsdl1.2debian-alsa                       1.2.13-1ubuntu1                                            Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa                            14.3.0-1.1build1                                           SoX alsa format I/O library
]0;jim@blackie: /home/jimjim@blackie:~$ head -1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Realtek ALC655 rev 0

And

> jim@blackie:~$ lsmod | grep snd
snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5617  1 snd_via82xx
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
jim@blackie:~$ sudo modprobe snd-via82xx
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.


Note, I did not run your script to upgrade alsa.  I wanted to be sure that it would be OK to do so on a new install of 10.04.

Note also I did a number of the same steps as reported by the other fellow with similar results.

Thanks for any help.

Jim.

---

### Post by lidex on 2010-07-25
The first thing to do with an upgrade is remove old config files. Try this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by JimGvo on 2010-07-25
> **lidex said:**
> The first thing to do with an upgrade is remove old config files. Try this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

It probably comes as no great surprise, but that didn't help.  I think it only found one file to remove.

Still don't have a speaker on the panel.  Is that some kind of clue as to which way to jump?

Thanks,
Jim.

---

### Post by lidex on 2010-07-25
Missing Panel Volume Icon:
Make sure these are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session indicator-sound
```

Right-click panel, select add to panel->indicator applet

---

### Post by JimGvo on 2010-07-26
> **lidex said:**
> Missing Panel Volume Icon:
Make sure these are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session indicator-sound
```

Right-click panel, select add to panel->indicator applet

Ah! When the speaker became viewable, it was muted.  I unmuted it and all is well.  I brought up alsamixer in a terminal window, but there wasn't a mute button on that panel.

Results of apt-get
0 upgraded, 0 newly installed, 7 reinstalled, 0 to remove and 0 not upgraded.

Thank you very much!

Jim.

---

### Post by lidex on 2010-07-26
You're welcome Jim. There are two layers with alsa being the sound base and pulseaudio the sound server that sits on top of it. Alsa was working fine but pulse was muting audio after that and you just didn't have the interface to unmute.

---

### Post by maxfan on 2010-10-04
I do not know if this is of any use but I have one of these sound cards arriving soon _ I only wanted it for the optical out socket If possible I will; popst the drivers somewhere if someone will err guide me how to do it

---

