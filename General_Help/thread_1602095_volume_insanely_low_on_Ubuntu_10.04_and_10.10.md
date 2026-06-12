---
title: "volume insanely low on Ubuntu 10.04 and 10.10"
date: 2010-10-21
forum: General Help
---

### Post by Joey Barclay on 2010-10-21
Ever since I duel booted my computer my sound on Ubuntu has been almost impossible to hear. I have turned up the sound all the way in the settings and in terminal by typing alsamixer. Is there anyway i can increase my volume because as of now I cant listen to music or watch videos.

---

### Post by Joey Barclay on 2010-10-21
Does anyone know how I can fix this?:(

---

### Post by 31632531 on 2010-10-21
I may be telling you to do something you've already tried, however, have you tried System>Preferences>Sound?

You should be able to boost your volume past 100% there (it also might be attenuating here.)

---

### Post by Joey Barclay on 2010-10-21
> **31632531 said:**
> I may be telling you to do something you've already tried, however, have you tried System>Preferences>Sound?

You should be able to boost your volume past 100% there (it also might be attenuating here.)

Yep already tried that:(

---

### Post by veggen on 2010-10-21
Had the same problem. Solved by opening alsamixer (or something alsa related) from console and cranked up all channels (or whatever they are called). All have nonsensical names, so just crank them all up.

I can't remember the exact command, but I know I didn't have to install any additional packages, it was in Ubuntu by default. Try Googling it up and/or check [this](http://ubuntuforums.org/showthread.php?t=205449).

---

### Post by Joey Barclay on 2010-10-21
I am wondering if my sound card is not fully supported. Heres what I know about my sound stuff Ubuntu says that my card or something is a hda-intel it also says something about sigmatel audio.

---

### Post by friTTe81 on 2010-10-21
Hmm alsamixer in terminal use to solve the problem for me, but dont crank them all to 100%.
Might get distorted then, i also got the hda-intel

---

### Post by Joey Barclay on 2010-10-22
here is some more of my information **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by michaelzap on 2010-10-22
Sounds like you're having the same (or similar) problem as I am, and so far I haven't figured out how to resolve it:
[http://ubuntuforums.org/showthread.php?t=870681&page=20](http://ubuntuforums.org/showthread.php?t=870681&page=20)

---

### Post by kalos on 2010-10-23
Joey, did you try alsamixer? (Not the system sound menu.)

I had [a similar problem]("http://ubuntuforums.org/showthread.php?t=1294942") (but that was back on 9.04). Essentially, I removed pulseaudio and installed alsamixer to pump up my volume. But I don't know if removing pulseaudio is a good idea anymore. Also, I do clean installs for each upgrade and have been satisfied with my sound volume for the last several releases.

---

### Post by Joey Barclay on 2010-10-23
> **kalos said:**
> Joey, did you try alsamixer? (Not the system sound menu.)

I had [a similar problem]("http://ubuntuforums.org/showthread.php?t=1294942") (but that was back on 9.04). Essentially, I removed pulseaudio and installed alsamixer to pump up my volume. But I don't know if removing pulseaudio is a good idea anymore. Also, I do clean installs for each upgrade and have been satisfied with my sound volume for the last several releases.

 "I have turned up the sound all the way in the settings and in terminal by typing alsamixer."

---

### Post by heldal on 2010-10-24
The program that manage sound (pulseaudio) sometimes gets confused wrt audio levels. I've seen this most often happen when switching back and forth to a low-latency alternative (jack) that is used for recording. The easiest way to get back to a known state without bothering about specifics about how to restart pulseaudio properly is to simply kill the pulseaudio process, remove the users-spesific pulse-audio-configuration (killall pulseaudio;rm -r $HOME/.pulse), then log out and back in.

---

### Post by Joey Barclay on 2010-10-24
> **heldal said:**
> The program that manage sound (pulseaudio) sometimes gets confused wrt audio levels. I've seen this most often happen when switching back and forth to a low-latency alternative (jack) that is used for recording. The easiest way to get back to a known state without bothering about specifics about how to restart pulseaudio properly is to simply kill the pulseaudio process, remove the users-spesific pulse-audio-configuration (killall pulseaudio;rm -r $HOME/.pulse), then log out and back in.

This problem has existed since 10.04 so I don't think it can be a pulse audio problem. My volume never sounded right.

---

### Post by heldal on 2010-10-24
> **Joey Barclay said:**
> This problem has existed since 10.04 so I don't think it can be a pulse audio problem. My volume never sounded right.

Ahhh. I thought it was a problem that showed up at some point on a previously working install. The problem with incorrect reference values in pulseaudio does persist across sessions, reboots, upgrades and even re-installs if the users homedir and its content is preserved.

The most likely causes if this isn't it is either that your system doesn't specify the proper options to the snd_hda_intel driver (supports many different soundcards), or that the mixer software isn't  controlling the correct channel. HDA-cards have many output channels, some of which may not be used on your system. [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) may be a place to start looking for additional information.

---

### Post by pmacdon on 2010-10-30
Bloody annoying, isn't it!

One fix is to enable the alsa preamp (after removing pulseaudio):

Just follow the directions at:

[http://alien.slackbook.org/blog/adding-an-alsa-software-pre-amp-to-fix-low-sound-levels/](http://alien.slackbook.org/blog/adding-an-alsa-software-pre-amp-to-fix-low-sound-levels/)

---

### Post by jilindi on 2010-12-30
I used the ALSA MIXER to successfully raise the volume from MythTV live TV feedback.

Press [Ctrl] [Esc]to open the Xfce Applications menu

In the Xfce Applications menu select the Mixer application
 - Select Multimedia/Mixer

In the Mixer application... 
 - Click [Select Controls] button
 - Enable "Master" and enable "PCM".
 - Raise the sliders and enjoy the sound

John L in Nebraska.

---

### Post by Joey Barclay on 2010-12-31
> **jilindi said:**
> I used the ALSA MIXER to successfully raise the volume from MythTV live TV feedback.

Press [Ctrl] [Esc]to open the Xfce Applications menu

In the Xfce Applications menu select the Mixer application
 - Select Multimedia/Mixer

In the Mixer application... 
 - Click [Select Controls] button
 - Enable "Master" and enable "PCM".
 - Raise the sliders and enjoy the sound

John L in Nebraska.

I would try it but I dont have Ubuntu anymore.

---

### Post by Joey Barclay on 2011-02-10
I did a reinstall on a different hard drive and the problem still persists it must be a non supported sound card.

---

### Post by ahnkle on 2011-04-24
Using (killall pulseaudio;rm -rv $HOME/.pulse) worked for me. I have hda-intel and the sound suddenly started being very quiet.

---

