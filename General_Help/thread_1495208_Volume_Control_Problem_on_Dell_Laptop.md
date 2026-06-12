---
title: "Volume Control Problem on Dell Laptop"
date: 2010-05-27
forum: General Help
---

### Post by sirious94 on 2010-05-27
So I have a Dell Inspiron E1705 running Ubuntu 10.04.  The speaker setup is a left and right speaker and what dell calls a "subwoofer" on the bottom of the computer.  The volume progression does not go from quiet to loud though,  it goes mute, then mute, then still mute, then all subwoofer, then progresses to all L/R speakers.  This means the only point that volume is relatively lower is in the middle, but it does not really go that low at all.  

How do I fix this?  Is there a program that progresses volume independent of the soundcard?  Is there a better sound driver that i can get for my computer?

Thanks in advance for any replies.

---

### Post by lidex on 2010-05-27
Try pulseaudio volume control. If not installed:
```
sudo apt-get install pavucontrol
```

Also this may help. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m27 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by Boompoet on 2010-06-20
I'm having the same issue and it didn't really work. I was able to get levels in the alsa control panel to where I wanted them and when turning up or down the volume with buttons on the front of the laptop, the volume just jumped right back up again. It is the oddest thing. It always worked in Ubuntu 8 and 9.

Any other thoughts?

Additional: I just fiddled with the settings in Gnome ALSA Mixer and it seems like the program is recognizing Master as the sub woofer, PCM as the master volume level, and PCM sounds like it's controlling base levels.

Any way to associate the PCM control with the buttons on the front of the laptop or the volume slider?

---

### Post by Boompoet on 2010-06-26
Got it. I added the following line to the alsa-base.conf.


> options snd-hda-intel model=ref

---

### Post by Dareth on 2010-08-26
I have the same computer model, this pretty much fixes it: [http://art.ubuntuforums.org/showthread.php?t=1317562]("http://art.ubuntuforums.org/showthread.php?t=1317562")

---

