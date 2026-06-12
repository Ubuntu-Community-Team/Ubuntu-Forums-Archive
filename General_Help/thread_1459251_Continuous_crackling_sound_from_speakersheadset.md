---
title: "Continuous crackling sound from speakers/headset"
date: 2010-04-21
forum: General Help
---

### Post by andygi on 2010-04-21
Hi
I've got some sort of problem with my sound configurations (I think). There's this crackling/disturbance (with an ocational beeping sound) coming from my headset whenever I insert a headset or speaker. Turning the sound off doesn't make it stop either.

I'm running Ubuntu 9.10 on a Acer Veriton 3600GT (some years old). Please note that I'm not all that familiar with Linux yet...

Typing aplay -l in Terminal returned the following:

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

You should also know that I've been googling around for an answer to this problem. I've tried a few "tricks" in Terminal with no luck (below)

1) Removing the last line in /etc/modprobe.d/alsa-base.conf and then restart.
(# Power down HDA controllers after 10 idle seconds 
options snd-hda-intel power_save=10 power_save_controller=N)
Source for this advice: [http://ubuntuforums.org/archive/index.php/t-1306567.html](http://ubuntuforums.org/archive/index.php/t-1306567.html)

2) add (to the same file) “options snd-hda-intel model=auto” without quotes at the end
Source: [http://monespaceperso.org/blog-en/2009/04/29/acer-aspire-6920-no-sound-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/04/29/acer-aspire-6920-no-sound-on-ubuntu-jaunty-904/)

3)Into Terminal:
sudo apt-get remove pulseaudio
sudo apt-get install esound
Here, I found myself unable to complete the rest of the procedure (Under*System -> Preferences -> Sound. Make sure they are all set to 'Autodetect'. The only one you will have to set manually to ALSA is 'Sound Capture' under 'Audio Conferencing'.
Under*System -> Preferences -> Sessions. Deselected or Remove the Pulseaudio Manager)
Source: [http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

Ummhh... having done this I (call me dumb, but...) installed GNOME ALSA Mixer from the Ubuntu Software Center.

I guess I'm WAY over my head here, so I would really appreciate some help

---

### Post by andygi on 2010-04-21
The sound has been a problem for me ever since I installed Ubuntu, so it wasn't my fault (at least in the first place).

---

### Post by P4man on 2010-04-21
silly question perhaps, but if you turn the machine on, do you have the same crackeling sound before ubuntu has booted ? If so, then its not a ubuntu problem, but crappy audio hardware and nothing will cure it other than buying an USB audio card.

---

### Post by andygi on 2010-04-21
I've thought of that... the crackling sound stops for a few seconds before the computer shuts down and when it boots, but then it starts again. It seems like the disturbance increases the more programs I'm running as well... the sound starts out low during boot, and then gets really annoying when I'm on i.e. youtube

---

### Post by andygi on 2010-04-21
I also recall the same problem with another computer I had a few years ago (ubuntu+laptop). Back then the sound worked fine with Windows XP, but not with Linux (one of those XP imitations that I cannot remember the name of)

---

### Post by andygi on 2010-04-21
Well folks... what DID work was to go back to the initial configurations and then insert another USB sound card. Thanks anyway.

---

