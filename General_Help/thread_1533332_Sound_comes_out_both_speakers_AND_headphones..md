---
title: "Sound comes out both speakers AND headphones."
date: 2010-07-17
forum: General Help
---

### Post by TheMaritimeMan on 2010-07-17
Hi all,

I'm running 32-bit Ubuntu 10.04 on an Acer Aspire 3050 laptop with a Realtek HD sound card. When I plug headphones in, the sound comes out of the headphones AND the built-in speakers, instead of the speakers muting as they should.

This happens on both the live CD and the installed OS which i'm running. I've tried every fix I can find on the Internet, including a setting changed in the text-mode ALSA Mixer, installing a package from synaptic, and other fixes for older versions of Ubuntu that can't be done on 10.04.

Any help with this matter would be greatly appreciated.

Thanks,
-Trent

---

### Post by TheMaritimeMan on 2010-07-18
Bump?

---

### Post by lidex on 2010-07-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by TheMaritimeMan on 2010-07-18
```
trent@ACER:~$ uname -a
Linux ACER 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
trent@ACER:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
trent@ACER:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-23-generic 2.6.32-23.16                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.23.24                                    Backported drivers for alsa-driver snapshot.
trent@ACER:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 2bfa

==> /proc/asound/card0/codec#1 <==
Codec: Realtek ALC883
trent@ACER:~$ 

```Well, at least now I know my sound card is a Realtek ALC883, haha.

Thanks,
-Trent

---

### Post by lidex on 2010-07-18
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by TheMaritimeMan on 2010-07-18
Thanks, but still no dice.

Now in alsamixer, whereas before it showed the headphone bar graph, now it shows no bar graph, although the word "headphon" is still there. Pressing up or down at the missing "headphon" graph doesn't do anything to it.

When I press F6, the choices I get are "(default)", "HDA ATI SB", or to enter the device name. I just chose default, since HDA ATI SB rings no bell to me.

In the Sound Preferences, everything is the same as before. The only device under the hardware tab is called "Internal Audio", and the available profiles are "Off", "Analog Stereo Input", "Analog Stereo Output", and "Analog Stereo Duplex". No matter which profile I choose, the problem is the same - sound still comes out of the speakers when I have headphones plugged in. (Although it comes out of the headphones, as well.)

Thanks,
-Trent

---

### Post by TheMaritimeMan on 2010-07-18
**Update:**

I found a "half fix", replacing the line "options snd-hda-intel model=acer" with "options snd-hda-intel model=targa-2ch-dig". Now sound comes out of the headphones only, but it truely comes *only* out of the headphones - if I unplug the headphones, the speakers do not work.

I'll put the "model=acer" line back in for future instructions on here.

-Trent

---

### Post by lidex on 2010-07-18
How many audio jacks do you have on this unit - analog and digital?
2 or 6 channel audio?

---

### Post by TheMaritimeMan on 2010-07-18
I am honestly not sure about the audio system in detail on this laptop - a friend gave it to me just a week ago.

I do know that it is both analog and digital. Is has 3 audio jacks on it, labeled Headphone/SPDIF, microphone, and line-in.

-Trent

EDIT: Oops, I see I never answered part of one of your posts above.
As stated in my first post, the laptop is an Acer Aspire 3050.

---

### Post by lidex on 2010-07-18
Replace that option line with this:
```
options snd-hda-intel model=3stack-2ch-dig
```
**Reboot**

---

### Post by TheMaritimeMan on 2010-07-18
Same result. I get the headphones without the speakers, but if I unplug the headphones, the speakers are still muted, and I get nothing.

Thanks,
-Trent

---

### Post by TheMaritimeMan on 2010-07-19
Bump.

---

### Post by lidex on 2010-07-19
Some more model options to try (append after =):
```
auto
3stack-dig
acer-aspire

```

---

### Post by TheMaritimeMan on 2010-07-19
> **lidex said:**
> 
Some more model options to try (append after =):
```

auto
3stack-dig
acer-aspire

```

A ha! "acer-aspire" did it!

```

options snd-hda-intel model=acer-aspire

```That was it! Now the speakers and headphones cooperate as they should!

Thank you very much lidex! I'll now be able to try out and completely enjoy my first linux-only computer! I am glad I don't have to try an older version of Ubuntu or another distro altogether!
-Trent

---

### Post by lidex on 2010-07-19
You're welcome! Now one last thing - would you mark the thread as solved please? Use 'Thread Tools' up top.

---

### Post by TheMaritimeMan on 2010-07-19
Done. I was going to do that but I forgot, haha.
-Trent

---

