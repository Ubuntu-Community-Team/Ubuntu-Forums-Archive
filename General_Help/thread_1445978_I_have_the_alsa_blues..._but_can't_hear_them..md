---
title: "I have the alsa blues... but can't hear them."
date: 2010-04-03
forum: General Help
---

### Post by schlitz100 on 2010-04-03
I'm running 9.10 64bit.
I am using spdif to a receiver for sound. The soundcard is built into the motherboard. I am using this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128072](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128072)

I was having issues playing DTS/Dolby in VLC/XBMC so I followed a guide and installed alsa and some libraries, switched the hardware option to analog stereo out and everything worked beautifully.

Then 2 days ago I installed a few updates (will post these later), java runtime, and torrent episode downloader and at one point in the day...

-I don't hear the splash screen sound on boot up.
-Anytime I load up non-DTS/AC3 video file in VLC a message comes up 'fixing avi index' then it plays w/o sound. No sound for mp3's.
-I can hear DTS and AC3 files perfectly but when I touch the volume slider button on VLC it turns into a red X
-on XBMC again videos with AC3 and DTS play perfectly, no sound from other video files or mp3s. 

I tried a few things I found online to help nothing worked. I found a guide for upgrading alsa to the newer version which I followed then lost all sound.

Everything installed correctly. Alsamixer shows all the levels are up, nothing muted. The new version shows up as installed. When running alsaconf it says 'No supported PNP or PCI card found. Probe for legacy ISA sound cards?' After I say yes a empty box pops up with an OK then when I click OK it goes back to the terminal with the errors listed below. 


jason@Sinistar:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jason@Sinistar:~$ alsamixer
jason@Sinistar:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr  2 2010 for kernel 2.6.31-20-generic (SMP).
jason@Sinistar:~$ sudo alsaconf
ERROR: modinfo: could not find module snd-opl3sa2
ERROR: modinfo: could not find module snd-cs4236
ERROR: modinfo: could not find module snd-cs4232
ERROR: modinfo: could not find module snd-cs4231
ERROR: modinfo: could not find module snd-es18xx
ERROR: modinfo: could not find module snd-es1688
ERROR: modinfo: could not find module snd-sb16
ERROR: modinfo: could not find module snd-sb8

Playing around with it, if i set the hardware to digital out it plays the splash sound on boot up I don't get any other sound after that. 


I am just really lost to where to go from here. Any help would be appreciated!

---

### Post by wbee on 2010-04-03
I know this is extreme.

If all else fails,see if the sound works with the live cd and if it does,reinstall it.

Sorry I can't be more helpful.

---

### Post by schlitz100 on 2010-04-03
I am so frustrated with it I am close to reinstalling but worried the same thing will happen again.

---

### Post by lidex on 2010-04-03
Do this for me please:
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by schlitz100 on 2010-04-03
[http://www.scribd.com/doc/29376369/Untitled](http://www.scribd.com/doc/29376369/Untitled)

---

### Post by lidex on 2010-04-03
One of these options added to alsa-base.conf may do the trick. I'm thinking 6stack-dig. The syntax is:
```
options snd-hda-intel model=6stack-dig
```

```
3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)

```

To edit:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add the line at the bottom. Save. Close. Reboot.

---

### Post by schlitz100 on 2010-04-03
I won't be able to try it for a couple of hours but thanks for taking the time. I will post results.

---

### Post by schlitz100 on 2010-04-04
still no sound

---

### Post by lidex on 2010-04-04
Out of those options posted previously, which seems like a close match for your system?

Edit: I inadvertently added a space in that line I posted. This is how it should look:
```
options snd-hda-intel model=6stack-dig
```

Try that.

---

### Post by schlitz100 on 2010-04-04
Still no sound. 6stack-dig seems like the best match.

(edit)
tried auto as well which didn't work.

---

### Post by lidex on 2010-04-06
Have you gone through this troubleshooting page for karmic:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by schlitz100 on 2010-04-06
I ended up reinstalling. I haven't messed with sound yet so I am where I was before messing with alsa initially. in VLC I can hear all files but DTS/Dolby doesn't crossover to my receiver and XBMC I get 'audio failed to initialize' on ac3/dts files and it plays stereo video files just fine. I can't find the guide I used last time to get everything working. I'm also wondering if I should remove pulseaudio this time around.

---

### Post by lidex on 2010-04-06
PulseAudio wiki:

> XBMC 

XBMC is an award winning media center application for Linux, Mac OS X, Windows and XBox. The ultimate hub for all your media, XBMC is easy to use, looks slick, and has a large helpful community...

XBMC 8.10 uses ALSA and an independant asound.rc which doesnt play well with pulseaudio but have native support for PulseAudio in SVN, which will be released along with XBMC 9.04. 

---

