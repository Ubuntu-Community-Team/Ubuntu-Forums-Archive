---
title: "ATI Radeon HD3200 HDMI Audio Problems"
date: 2010-04-16
forum: General Help
---

### Post by Native Dialect on 2010-04-16
Salutations kind folks,

I have been attempting to troubleshoot this issue for an hour now. My HDMI port (through the ATI Radeon HD3200), is not playing any audio for videos that are watched through a web browser (e.g. Hulu, Youtube). I get HDMI audio for programs on the computer itself (e.g. playing a song in Amarok or Dragon Player). I have tried a bevy of solutions

- Purging the existing flash installation
- Installing new plugin (sudo apt-get install flashplugin non-free)
-Adjusting the volume control and sound preference
-Selecting IEC958 from the switches tab

I am at my wits end with the terminal and plugins and drivers. Any insight or  thoughts on techniques I may have overlooked, will be greatly appreciate. Thank you all in advance (and subsequent thank yous will follow, where appropriate).

---

### Post by Native Dialect on 2010-04-16
Any help or suggestions? Please.

---

### Post by Native Dialect on 2010-04-17
Somebody has to know how to resolve this. The Gateway NV52 is a semi-popular laptop choice. I know others had to of had this problem. Anyone, please help?

---

### Post by chris.jericho on 2010-04-17
okay.... so videos work (like on Youtube) but you can't here the audio right? is that your problem?

---

### Post by Yellow Pasque on 2010-04-17
Maybe this will help: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by Native Dialect on 2010-04-17
> **chris.jericho said:**
> okay.... so videos work (like on Youtube) but you can't here the audio right? is that your problem?

That is correct. I plug in my HDMI cable, and I can see things fine on my HDTV. Unfortunately, the sound comes out of my laptop speakers, rather than through my HDTV. Except, this is only when it comes to things I watch or listen to online. If the video file or song is on my computer itself, the sound will come through my HDTV, as it should.

@Temujin

I tried that option, and I thank you, but it did not resolve my issue :(


Does anyone else have any other suggestions?

---

### Post by Native Dialect on 2010-04-18
I figured it might be useful to provide specifics about my sound hardware 

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
lucidfox@lucidfox-laptop:~$

---

### Post by Native Dialect on 2010-04-18
Also, I already installed the GUI Alsa Mixer. That has not helped out either.

---

### Post by gradinaruvasile on 2010-04-18
Your problem is likely the flash player. That thing has a mind of his own.
One thing you could try is to install pavucontrol, and route the playing streams through HDMI. Right-click on the stream and you have a choice there to send it to the output device of your choice.

---

### Post by Native Dialect on 2010-04-18
I uninstalled Pulse Audio, yesterday. I thought there might have been a chance that it was causing a conflict with ALSA. Under the sound preferences, my HDMI was linked to ALSA and OSS. Should I reinstall Pulse Audio and give that controller a a chance?

---

### Post by Native Dialect on 2010-04-18
> **gradinaruvasile said:**
> Your problem is likely the flash player. That thing has a mind of his own.



This turned out to be the reason. I thought it was the browser and it wasn't. As it turns out, AVI files that I watch or WAV files, play just fine in Firefox, over HDMI. The problem is Shockwave (Flash). 

That really grinds my gears, as I am not sure if there is a way to have Firefox use Flash for the video component, but use some other audio codec for FLV audio. But I appreciate that thought, that the problem was Flash itself. It caused me to explore the problem from a different angle, and see if it was isolated to Flash or the whole browser.

---

### Post by the_pod on 2010-11-26
Ever find a solution for this?  I had one, but it was a year ago.  Am rebuilding my box and don't recall what I did to fix things.  (But there is a way to do it that isn't a pain - I had Hulu Desktop, AOL streaming radio... all kinds of good stuff).

Back to the Google.

---

