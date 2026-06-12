---
title: "No Microphone / USB Onboard Sound Card  10.10/Ubuntu"
date: 2010-12-06
forum: General Help
---

### Post by Sxynerd on 2010-12-06
I had gotten it to work one time a few weeks ago but it does not work anymore.  IDK why.

I am trying to use an onboard sound card in a HP desktop model number A6600F.  

Before I installed my graphics card yesterday I had a bunch of options for "System/sound/hardware", too many in fact and it took a lot of selecting to figure out which one worked.  Now I have two or three options.

One of the options says ATI HDMI but my V card does not have HDMI and as I said, I am trying to use my motherboards Onboard audio.

I have no idea what any of this means but doing a search on here, I found these commands to post.  I also did download Gnome-Alsamixer with no luck.
> **micahel@10:~$ uname -a**
Linux 10 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux
**micahel@10:~$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**micahel@10:~$ cat /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.23.
micahel@10:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card2/codec#0 <==
Codec: ATI R6xx HDMI
**micahel@10:~$ **


---

### Post by Finn bjerke on 2010-12-07
I have terrible mic problems on my laptops. 
 
1. Toshiba satelite 130 laptop: no mic input despite installing pulse-audio and/or Pavu Control. I use line in for the jack based mic. 
2. Compaq PC: crackling sounds after installing Pulseaudio, terribly noisy. No specific mic control. I use line in for the jack based mic. 
 
My desktop PC: works great no matter what pickup I use. its a Fujitsu something. I use line in for the jack based mic. 
 
This has been a problem for Ubuntu Linux for yrs. I suggest the problem is taken care off, this is more important imho than nwew Ubuntu versions every 6 month. A PC with no functional mic is no good! 
 
1. Its a soundcard problem so we need a list of soundcards that actually works qwith Ubuntu (10.10 that is)
2. USB mics does not use soundcards so we need a list of good USBbased mics (including wirelesss headsets) 
3. The "launchpad" bug fix forum is just horrible. Not user freindly at all, ID rather navigate dead drunk in the amazonas at night than find anything usefull there, also its not in the "Ubuntu-spirit" to close down threads becouse noone answers them for a while, the thread just "reincarnates" Bux fixes is a serious matter imho.
 
Usefull "workarounds" so far:
 
1 Install pulseaudio and see to that the mic (which is a mono device) uses only left channel
2. Use ALSA mixer
3. USe PAVU control 
4. Others ? 
 
Frankly Im frustrated by this and I must confess I find the "Ubuntu 11.04 hype" highly irrelevant until this problem is solved.
 
What about stereo mics ??

---

### Post by Finn bjerke on 2010-12-08
I now use a bluetooth device for micing skype. Works well and iots wireless which is nice.

---

