---
title: "nvidia 570 GTX evga wont play audio over HDMI"
date: 2011-01-14
forum: General Help
---

### Post by kvcckid on 2011-01-14
Hello, I recently built a new computer and got an evga 570GTX (Nvidia)
I was using windows 7 pro that I got for free from school (MSDN or something) but it was crashing every 5 minutes.  I could get on a play a game for 4 hours, but cuz cursing around or surfing the web was crashing all the time.  Complete freeze.  Couldn't start the task manager, number lock and caps lock jammed ect...

I was starting to think it was my MOBO failing because of the reviews until I installed ubuntu and everything was fine, no crashing no bull$#!7 no evil sauce.

Only problem was I installed 10.04 and fought it for a day with no luck installing the graphic card drivers but today I installed 10.10 and it picked up the nvidia drives right away.

Now the only problem I am having is audio.

In Windows I could play audio over the HDMI cable but in ubuntu I cannot.

I've tried using a headphone cable and that doesn't work either, and I know it's not the cable or the green sound port on my MOBO because other speakers work in the port, headphones work, all the cables work ive tested them on other computers and speakers and in cars, so the only thing left is the OS.  I want to be able to play audio from the computer over the hdmi cable to the TV.  

I've played around in the sound settings for hours... NOTHING.

I dont get how something as simple as audio over HDMI or a headphone jack/cable can be done by windows and not UBUNTU!!!

---

### Post by efflandt on 2011-01-14
What do you get for output of:

**dmesg | grep -i hda** (small i as in case insensitive)
**aplay -l** (small L)

Does **alsamixer** show S/PDIF devices if you press F6 and go to HDA NVidia?  Once we know those things we can tell if all you need to do is unmute them, test which one works, and add something to /etc/pulse/default.pa to be able to select the proper device from Sound Preferences.

I have a GT 430 and am not sure if the GTX 570 does HDMI sound any differently, but different nvidia cards may use different card# and device#.

---

### Post by kvcckid on 2011-01-14
dmesg | grep -i hda returned 

user@LinuxBox:~$ dmesg | grep -i hda
[    8.720318] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.075377] hda_codec: ALC892: BIOS auto-probing.
[    9.084455] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.084458] hda_intel: Disable MSI for Nvidia chipset
[    9.084497] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.353259] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
user@LinuxBox:~$ 


and 
aplay -l 
returned
 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


also where do I find alsamixer? Is that the sound settings? and where do I press f6? in alsamixer or the terminal?

---

### Post by kvcckid on 2011-01-15
the nvidia card is showing up in the sound preferences and I can select it as an output but it does nothing.

---

### Post by efflandt on 2011-01-16
Run **alsamixer** in a terminal.  Then press F6 to select HDA NVidia and unmute all the S/PDIF devices by pressing m for any that are muted, so they all show 00 instead of MM.

Then try the following, substituting 1,3 with 1,7 1,8 or 1,9 until you find one that works:

aplay -D plughw:**1,3** /usr/share/sounds/alsa/Front_Center.wav

For example the one that worked for me was 1,9 so I added a line to /etc/pulse/default.pa after the alsa sink line:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Then reboot and try playing Rythmbox and see what happens when you switch Output devices in Sound Preferences.  Note that HDMI might be one that does NOT say HDMI.

---

### Post by kvcckid on 2011-01-17
> **efflandt said:**
> Run **alsamixer** in a terminal.  Then press F6 to select HDA NVidia and unmute all the S/PDIF devices by pressing m for any that are muted, so they all show 00 instead of MM.

Then try the following, substituting 1,3 with 1,7 1,8 or 1,9 until you find one that works:

aplay -D plughw:**1,3** /usr/share/sounds/alsa/Front_Center.wav

For example the one that worked for me was 1,9 so I added a line to /etc/pulse/default.pa after the alsa sink line:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Then reboot and try playing Rythmbox and see what happens when you switch Output devices in Sound Preferences.  Note that HDMI might be one that does NOT say HDMI.


Okay so I did what you said, popped open a terminal window and ran alsamixer and I got [ATTACH]181365[/ATTACH]

so I pressed f6 and selected HDA NVidia and I got [ATTACH]181366[/ATTACH]
then I did what you said, used my arrow keys to move my selection and press m to toggle the ones that said mm to 00.
[ATTACH]181367[/ATTACH]

Now if I exit terminal and rerun alsamixer, repress f6 ect... they have stayed changed to 00 so I did not need to save the settings.

Now do I just enter ```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```
in a terminal window or in the area that alsamixer brings up? also do I have to reboot for each option I try?

Thanks again, i'm one step closer.

---

### Post by kvcckid on 2011-01-17
okay hot dog, I ran ```
 aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav 
```

and it jumped me because I was not expecting my TV to scream FRONT; CENTRE at me at full volume.

Now do I add that to the file with the terminal or just by editing the file with txt edit?

---

### Post by kvcckid on 2011-01-17
okay the audio is working but it sounds like it's got some static or mechanical whining/white noise with cretin pitches, any way to fine tune this?

---

### Post by kvcckid on 2011-01-17
sorry for the triple post; audio is working but with that feed back junk-y sound. 
I have to run ```
 aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav 
``` after ever reboot because 
```
#load-module module-alsa-sink
load-module module-alsa-sink device=hw:1,9 
```
Is not working

any ideas on how to fix the two?
Thanks again for all your help

---

### Post by efflandt on 2011-01-19
Since 1,7 works for you, that is what you need to use instead of the 1,9 that worked for my GT 430.

Do **gksu gedit /etc/pulse/default.pa** (or **sudo nano /etc/pulse/default.pa** ), look for the commented out line **#load-module module-alsa-sink** then add the following line after it (without #):
[FONT=monospace]
[/FONT]```
[FONT=monospace]load-module module-alsa-sink device=hw:1,7[/FONT]
```[FONT=monospace]Reboot, play some music, and see if one of the Outputs in Sound Preferences works for HDMI audio (you can switch Output on the fly).  But it might not be the one that says HDMI.

Then you might want to go to **alsamixer** and **mute** "S/PDIF 2" and "S/PDIF 3" for HDA NVidia, because I think S/PDIF is always unmuted by default and "S/PDIF 1" is the only one you need for card 1, device 7.
[/FONT]

---

### Post by kvcckid on 2011-01-19
okay I figured out what you meant; I found the file and found the line I need to change, currently it is 1,0 and I need to change it to 1,7 but the file is read only and I can not give myself permissions. I've being Google-ing how to do this in terminal or log in as root but can not find that.

---

### Post by kvcckid on 2011-01-19
> **efflandt said:**
> Since 1,7 works for you, that is what you need to use instead of the 1,9 that worked for my GT 430.

Do **gksu gedit /etc/pulse/default.pa** (or **sudo nano /etc/pulse/default.pa** ), look for the commented out line **#load-module module-alsa-sink** then add the following line after it (without #):
[FONT=monospace]
[/FONT]```
[FONT=monospace]load-module module-alsa-sink device=hw:1,7[/FONT]
```[FONT=monospace]Reboot, play some music, and see if one of the Outputs in Sound Preferences works for HDMI audio (you can switch Output on the fly).  But it might not be the one that says HDMI.

Then you might want to go to **alsamixer** and **mute** "S/PDIF 2" and "S/PDIF 3" for HDA NVidia, because I think S/PDIF is always unmuted by default and "S/PDIF 1" is the only one you need for card 1, device 7.
[/FONT]


I was doing that and it was not working and then I re-read your post and saw that I was editing the line below the one I was meant to because it looked like this 

```
 #load-module module-alsa-source device=hw:1,0 
```

but then I found the correct one above and added the part you said to.  About to reboot now, I'll let you know how it goes

---

### Post by kvcckid on 2011-01-19
ROCK'N ROLL!!!!

It's working great and that Stacie/white noise is gone after muting SPIDF2+3

although sound test does not work in preferences.

Thanks so much.

---

### Post by eshwar_andhavarapu on 2011-01-25
> **kvcckid said:**
> ROCK'N ROLL!!!!

It's working great and that Stacie/white noise is gone after muting SPIDF2+3

although sound test does not work in preferences.

Thanks so much.

Thanks people!! This really helps! I wonder why we need the manual workaround given that Nvidia is not a new thing to linux.

---

