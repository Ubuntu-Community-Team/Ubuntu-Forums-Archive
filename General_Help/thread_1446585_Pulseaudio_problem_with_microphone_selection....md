---
title: "Pulseaudio problem with microphone selection..."
date: 2010-04-04
forum: General Help
---

### Post by acron1 on 2010-04-04
AlsaMixer by default selects "Mic" as the microphone input for my Toshiba Satellite T115D-S1125 see pic below:

[IMG][[IMG]http://img163.imageshack.us/img163/9983/13595117.png[/IMG]](http://img163.imageshack.us/i/13595117.png/)[/IMG]

I need to select "Mic 1" but as soon as I do the mic is muted in Sound Preferences see below:

[IMG][[IMG]http://img641.imageshack.us/img641/7564/30465868.png[/IMG]](http://img641.imageshack.us/i/30465868.png/)[/IMG]

For a brief moment I can see activity from the input level display and then nothing...
I have tried removing PulseAudio and that has worked but I prefer to correct this with PulseAudio installed as it seems to be a simple fix...

Thanks for your help.

---

### Post by acron1 on 2010-04-05
Update:

I can use Audacity and select "Mic 1" and record without a problem using HDA ATI as the device of choice...
But as soon I select Mic 1 Sound Preferences mutes the Mic...

[[IMG]http://img265.imageshack.us/img265/9671/screenshott.png[/IMG]](http://img265.imageshack.us/i/screenshott.png/)




[[IMG]http://img62.imageshack.us/img62/6752/screenshotaudacityprefen.png[/IMG]](http://img62.imageshack.us/i/screenshotaudacityprefen.png/)

I know Pulseaudio is problematic however does anyone have any ideas?















;

---

### Post by acron1 on 2010-04-08
Any ideas?
Anyone?...

---

### Post by derekeverett on 2010-04-08
I know this probably isn't the solution your looking for.. but all I can do is tell you what I did.

I switched to Debian and all my microphone problems went away.

I have posted numerous threads in these forums with a similar question. Never did get it figured out. After months of frustration I tried Debian and it worked "out of the box" so to speak. I just had to turn the external mic volume up, which was nothing.

Good luck.

---

### Post by gradinaruvasile on 2010-04-08
> **acron1 said:**
> Any ideas?
Anyone?...

Install Debian. I did it too and everything works as expected.

On your specific problem in a nutshell: Ubuntu has a crappy implementation of PulseAudio.
More elaborate:

The current sound system works this way: ALSA is the "low-level" sound system in Linux (its a de facto standard).
PulseAudio is a software mixer that can run on top of ALSA - It is a bit confusing because it can collect the sounds from the ALSA sources (if the program in question uses ALSA only) and process them once more, but it can be accessed directly (but the effective sound grabbing/playing is done through ALSA eventually anyway).

The good:
The idea of PulseAudio is great - it offers an interface to route sound streams between multiple sound sources (even via bluetooth/USB), modify sound levels on the fly separately for applications, configure the sound cards available easily. just look at the sound control applet, it is a simple to use interface that offers great control over the sound devices.

The bad:
The implementation, however, is not that good as the idea. The problem comes from the fact that the PulseAudio server needs to interface itself with ALSA calls - there are many applications that use ALSA differently, some of them use methods that in theory should not work, but they do work with ALSA. The PulseAudio devs claim that they implement the documented ALSA methods correctly (by the letter so to speak) and that ALSA is to blame beause allows for non standardised methods to work. But many programs are already written for years and they wont change easily/at all. 

This Ubuntu-specific embedding of PulseAudio creates many problems of its own on top of PA's own: You cannot bypass the PA server (only OSS using apps can do that, blocking sound from other applications) effectively - many apps that use ALSA+non-standard methods either lose sound, either it is crippled/skipping, either crashes the PA server sometimes. And if you uninstall PulseAudio you will be left without volume control applet. Not nice.

In Ubuntu, the devs wanted to make it easy for the users by providing one simple interface to rule them all sound devices. That is naturally PulseAudio. No problem here. 

The problem is that the devs know about the issues for years. PA is around from 8.04. And had many users angered. But they pushed PA regardless as the primary sound system. They knowingly chosen more features over stability.

Now, PulseAudio exists in other distributions (probably all) and works better than in Ubuntu. Why? Because it is not that tightly integrated and apps that want to use ALSA specifically are permitted to do so. Ad if someone doubts it, i had PA using program (via bluetooth, doing SIP echo test) running alongside playing a movie via ALSA via the internal sound card in Debian Testing.

I switched to Debian Testing for some time from Ubuntu (PA and similar dev decisions made me do it + the unease of 6 months upgrades).
Debian comes with ALSA pre-installed by default. PulseAudio is optional. I use 3 computers, 2 desktops, 1 laptop. On the desktops i use ALSA only because i dont have exotic (USB/Bluetooth/Add-on etc) sound cards. Zero sound problems.
On the laptop i use bluetooth handsfree with Skype/SIP programs. So i need PulseAudio because ALSA over bluetooth doesnt work consistently. I installed it and i have no problems (that i had with Ubuntu). I made a plugin in ALSA that makes possible to route sound from ALSA to PulseAudio (extended ALSA devices support is needed though). And one uncommented line and the audio is routed through PA.

---

### Post by lidex on 2010-04-08
You may want to check your settings in alsamixer. Terminal command: ```
alsamixer
```
Press F4 for capture devices. Look for "Input Source" or text only entries. Scroll with left/right arrow keys. Toggle source with up/down keys. F6 selects sound card.

Also check "Input Devices" tab in pulseaudio-volume-control.

---

### Post by derekeverett on 2010-04-08
> **lidex said:**
> You may want to check your settings in alsamixer. Terminal command: ```
alsamixer
```
Press F4 for capture devices. Look for "Input Source" or text only entries. Scroll with left/right arrow keys. Toggle source with up/down keys. F6 selects sound card.

Also check "Input Devices" tab in pulseaudio-volume-control.

This is good advice. However, I have beaten my head against that wall many times. It becomes very frustrating when nothing seems to work.

---

