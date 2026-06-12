---
title: "No Sound for 9.10"
date: 2010-02-26
forum: General Help
---

### Post by donuthead7310 on 2010-02-26
Hey guys.

I've seen just about every thread about this topic in the forums, tried just about any fixes, but have come across nothing.

I have no sound for Ubuntu 9.10, and it's really frustrating me.  The thing is that the sound works coming out of my laptop speakers, but not my headphones.  My headphones work fine, I checked them.

Help, please?

---

### Post by lidex on 2010-02-27
That thread title is a bit misleading - you'll want  to be more concise to make sure you get the proper help.
Can you post the output of these terminal commands please:
```
cat /proc/asound/version
```
```
uname -a
```
```
aplay -l
```
```
head -n 1 /proc/asound/card0/codec*

```

You can find a terminal in Applications Menu: Accessories>Terminal

---

### Post by lidex on 2010-02-27
I stole this from soundcheck's alsa upgrade thread (linked to in my sig):
> Before reporting "NO SOUND" problems - check if your alsamixer-channels are activated and unmuted (gnome-mixer/volume-control/preferences)!!
Very often there are headphone-jack, Toslink, SPDIF or microphone issues reported. Usually this has something to do with wrong alsamixer settings or more seldom with a wrong model-id assigned to your sound-driver in /etc/modprobe.d/alsa-base.conf .
If you're lacking certain controls in alsamixer or your driver is not even being loaded, you should check-out your model-id in attached HD-Audio-Models.txt.
I strongly recommend to try similar model-id's matching your codec to checkout if your faulty function gets working.
I'd guess 80% of the reported problems (group: other than alsamixer issues) over here are related to the model setting in alsa-base.



---

### Post by donuthead7310 on 2010-02-27
For cat /proc/asound/version

 I got:

Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Jan 28 2010 for kernel 2.6.31-19-generic (SMP).

For uname -a

I got: 

Linux Joshs-Computer 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

For aplay -l

I got:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

For head -n 1 /proc/asound/card0/codec*

I got:

==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9205

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

---

### Post by lidex on 2010-02-27
What's the make and model of your laptop?

---

### Post by tpho2500 on 2010-02-27
I too have this problem..maybe you can help us both since this is the same?


cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.20.

uname -a

Linux thanh-phong-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

head -n 1 /proc/asound/card0/codec*

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC268

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054

---

### Post by garvinrick4 on 2010-02-27
Re: No sound after upgrade to Karmic Koala 9.10
Did 3 installs or upgrades to 9.10 and this worked each time. 9.10 Just have to do
Part A. Just follow instructions. REBOOT WHEN DONE.

sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio


Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.
9.10
1. Backup (and then delete) your previous configuration files:
Code:

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound*
$ sudo rm /etc/asound.conf

Warning: As always, use caution when removing files on your system. Any typos can potentially cause data loss.
Note: Don't worry if some of these files did not exist on your system.


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:
Code:

$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

3. Ensure the evil "libflashsupport" library is not installed:
Code:

$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
Code:

$ pulseaudio & pavucontrol

6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):

Code:

$ alsamixer -Dhw

Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.

7. Continue to Part B if you are running Hardy Heron (8.04), or Part C if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effec

---

