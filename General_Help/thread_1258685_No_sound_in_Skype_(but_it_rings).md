---
title: "No sound in Skype (but it rings)"
date: 2009-09-05
forum: General Help
---

### Post by Lockheed on 2009-09-05
When I make a testcall, I can hear the initial dialing sound and then waiting tone, but as soon as the other side picks up, I cannot hear a thing.

When this mute call is in progress and I try to start some other audio app, i.e. play a movie in mplayer, I get no sound in this player. I need to stop the call and restart mplayer to recover sound.

Also, whenever I try to use Sound Recorder, it tells me the settings for audio capture are incorrect.

I tried all combinations in Skype sound options but to no avail.

I am using:
- newest skype from Medibuntu repositories
- onboard ES1869 sound card (Compaq Dekspro EN, Pentium II 400Mhz)
- LXDE and ALSA

---

### Post by P4man on 2009-09-05
how new is the newest in the medibuntu repo's?
The latest is Version 2.1.0.47 and it came out only a few days ago, after a long 2+ year wait. It *finally* supports pulseaudio. If you got the previous version, remove it and try the new (beta) from skype's website:

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

edit: oh, you use alsa. Well, I think it still supports alsa, but it might have the same problem, im not sure.
You could try the dynamic static version though (what a name, hu? :) )

---

### Post by Roasted on 2009-09-05
I got really excited. Then I saw:

Ubuntu 8.04
Ubuntu 8.10+ 32-bit
Ubuntu 8.10+ 64-bit 

Dear Skype developers. Hi. Welcome to Sept 2009, the age of Jaunty.

I tried to install 8.10 64 bit anyway on top of my 9.04 64 bit install and it errored out.

:(

---

### Post by P4man on 2009-09-05
> **Roasted said:**
> I got really excited. Then I saw:

Ubuntu 8.04
Ubuntu 8.10+ 32-bit
Ubuntu 8.10**[COLOR="Red"]+ [/COLOR]**64-bit 

Dear Skype developers. Hi. Welcome to Sept 2009, the age of Jaunty.

I tried to install 8.10 64 bit anyway on top of my 9.04 64 bit install and it errored out.

:(

note the plus. It means it requires 8.10 or later. Not sure why it doesn't install for you though, works great on 3 jaunty's ive installed it on...

---

### Post by Roasted on 2009-09-05
I get an error regarding -

trying to overwrite /usr/share/icons/skype.png, which is also in package skype-common.

I had the older version of skype installed and uninstalled it. Now I'm trying to install this deb package of the new version of skype on it. I even deleted the skype.png icon out of the /usr/share/icons folder and it still errored out.

---

### Post by P4man on 2009-09-05
looks like it didnt uninstall completely ? Dont know, never installed from the medibuntu repo's. Since skype does an update for linux like once every 2 years, I fail to see the point ;).

Id check in synaptic if there are still traces of skype somewhere?

edit: btw, afaicr, i didn't uninstall before installing...

---

### Post by Lockheed on 2009-09-05
It is 2.0.0.72. I tried using Skype from their webpage but it quits seconds after I run in (Segmentation error).

Anyway, **_lets get back on the topic of this thread_.**

---

### Post by Roasted on 2009-09-05
> **Lockheed said:**
> 
Anyway, **_lets get back on the topic of this thread_.**

whoa there, killer. We actually are on topic.

I was having issues with my skype sound. As a result, I'm taking what was recommended to another user here (you) in the exact same situation - upgrade skype. 

Staying on topic... I ran a sudo apt-get remove --purge skype, but it found nothing. I checked synaptic as recommended by P4man and sure enough, skype-common was there. Did a complete removal and presto, Skype installed from the deb accordingly.

Thanks doods. Hope the new version fixes your issue Lockheed.

---

### Post by Lockheed on 2009-09-05
Well...
1. I tried newest skype before even adding medibuntu repositories so the system was skype-clean.
2. It's not the installation I had problems with, but running it. Newest skype installed just tip-top but quits seconds after starting the program.
3. I do think we are off the topic because I am pretty sure those audio issues are not restricted to any particular version of skype.

---

### Post by Lockheed on 2009-09-08
Bump

---

### Post by Roasted on 2009-09-08
What are your sound settings in System - Preferences - Sound.

---

### Post by Lockheed on 2009-09-08
No such menu. I am using LXDE on that computer.

---

### Post by Roasted on 2009-09-08
Yick... never heard of it so I have no idea where the sound preferences would be...

Is there any sort of preference menu you can get to? A control panel perhaps? Anything where you can dig up sound preferences is what I'm curious to see.

To the best of my limited knowledge, I understand that your Skype sound settings have to match what sound settings you have on the system itself. Which would make sense. If your system is using ABC settings, Skype won't work with XYZ settings. Worth a shot. Post back if you dig up the settings.

---

### Post by Lockheed on 2009-09-08
Well, I can use alsamixer and its gnome version.
The problem is, however, I tried all possible settings in Skype with no luck.

I think the underlying cause is related to the fact that I cannot record anything with the computer because when I turn on ubuntu's stand-alone sound recorder, it tells me it cannot start because recording settings are wrong.

Then again, I don't know where else can I poke around for those settings.

---

### Post by Roasted on 2009-09-08
I'm a bigtime gnome fanatic, so without you being on gnome I'm kind of limited in terms of how I can help... I always test audacity for sound recording. Just recently when my microphone in skype didn't work I couldn't figure out why. Turns out in my sound preferences there was a menu for it where it was disabled. Audacity worked afterwards and so did skype.

---

### Post by Lockheed on 2009-09-09
Nope. mic is enabled everywhere.

---

### Post by Lockheed on 2009-09-12
Bump

---

### Post by pdc124 on 2009-09-13
whats the output  if you run skype from  a terminal ?

---

### Post by 3rdalbum on 2009-09-13
Skype uses Pulseaudio when available; does your system have Pulseaudio?

In order to configure Pulseaudio, you need to install the padevchooser package, and then run the program (which appears in your notification area). Start Skype and do the Test Call. Go to the padevchooser, left-click and choose Volume Control.

Now under "Playback" and "Recording", it gives you the volume control for Skype. There's a little arrow next to it that opens a popup menu where you can change the audio device. Change it to your headset/microphone. Now Skype will always use those devices unless they are unplugged.

Padevchooser solves 95% of all Pulseaudio complaints, no idea why Ubuntu doesn't ship with it.

---

### Post by pdc124 on 2009-09-13
in the pavdevchooser i have no option for skype under the recording tab

---

### Post by Lockheed on 2009-09-13
> **pdc124 said:**
> whats the output  if you run skype from  a terminal ?

```
~$ skype
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
```


[QUOTE=3rdalbum]Skype uses Pulseaudio when available; does your system have Pulseaudio?[/QUOTE]
No, I do not have pulseaudio. I am using ALSA. The soundcard is an old ISA mobo-integraded ESS1869 card which uses module ES18xx. It took me a week to make this thing work with ubuntu and ALSA.
I think it's not a good idea to pair such card with PulseAudio. Do you?

---

### Post by pdc124 on 2009-09-13
looks similar to my problem - and i have tried with and without pulseaudio
[http://ubuntuforums.org/showthread.php?t=1259322&highlight=skype+sound](http://ubuntuforums.org/showthread.php?t=1259322&highlight=skype+sound)

---

### Post by celem on 2009-09-13
Thanks P4man, just loaded the new version direct from Skype and it works great on my Ubuntu 9.04 amd64 desktop.

---

### Post by Lockheed on 2009-09-14
I installed Pulseaudio. I followed the HOWTO guide and then chose "pulse" everywhere in Skype. 

Now, when I call testcall, I can hear the sound but it is very choppy and Skype uses 100% of CPU. Granted, it's only PII 400Mhz but that's not justified.

Also, I still cannot record anything. When the lady tells me to start speaking and then the call continues to playback of what I said, the call ends.

Also, throughout the duration of the call, I am getting this from Skype console:
```
RtApiAlsa: underrun detected.

```

---

### Post by Lockheed on 2009-09-15
up

---

### Post by Lockheed on 2009-09-16
Here is what I get when I try to test recording in Sound Properties:

```
Error running pipeline 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat': 
Could not configure support library. [gsthalaudiosrc.c(167):
do_toggle_element (): /GstPipeline:pipeline0/GstGConfAudioSrc:gconfaudiosrc0/GstBin:bin2/GstHalAudioSrc:halaudiosrc0:
Failed to render audio source from Hal]
Segmentation fault

```

---

### Post by Lockheed on 2009-09-19
I really need a hand with that.

---

### Post by Lockheed on 2009-09-24
Bump once more

---

### Post by Lockheed on 2009-09-29
up

---

### Post by Lockheed on 2009-09-30
Come one, guys. I need to solve it in the next few days. Then, I'll leave for months and my mum won't be able to call anyone with Skype.

---

### Post by Lockheed on 2009-10-03
up...

---

### Post by ozzywin on 2009-10-03
Not sure if this will help but I followed this and it worked
[http://annevankesteren.nl/2008/04/ubuntu-microphone](http://annevankesteren.nl/2008/04/ubuntu-microphone)

---

### Post by GJCT on 2009-10-04
Hi, I'm having a similar problem.

All my other audio works fine, but when I start a skype call, I hear the ring, and then nothing (no voice from the test call). I did what 3rdalbum suggested in this thread and got it to work once, but no more. 

When I start the test call and open padevchooser, nothing shows in playback or recording. Then, after hanging up the test call, if I start another test call I don't even hear the ring. :confused: 

Then if I try to shut down skype, it won't quit, and I eventually have to kill the process to get it to shut down.

I'm using Jaunty (9.04) and in my skype settings all is set to PulseAudio Server (local).

Any help would be HUGELY appreciated!

---

### Post by Lockheed on 2009-10-04
We have the same problem if you are unable to record anything with gnome sound recorder. Whatever I do, nothing is being recorded.

I tried fixing it on both ALSA and PulseAudio. Overall, there is no difference if I use one or the other.
In Pulse's devie monitor, I can see the spikes in microphone input (Pulse IS hearing the microphone) but nothing is being recorded.

Anyways, I tried everything I was able to find with google and on this forum but no form of recording is working on my ubuntu.

---

### Post by GJCT on 2009-10-04
Well, I can record and playback my recording with sound recorder, and it works fine, but, while I am recording, nothing shows up under the "recording" tab of the padevchooser programme. I understand that it should show the levels.

---

### Post by keithp on 2009-10-04
Same here.

The mic doesn't work in either Skype or aMSN. (Ubuntu 9.04 or Ubuntu 9.10)

I've tried for some time to sort the problem, but no luck.

I regularly do Skype or MSN video/audio chats, but until sound works, I have to use Windows. 

Keith

---

### Post by GJCT on 2009-10-04
On my sound settings (preferences) everything is set to Autodetect, except sound capture, which is set to my sound card (VIA8233) Asla. When I click test it works (there is no sound, but I assume this is because it is a capture). When I try and set it to Pulse Audio Server and test it, I get the error: 

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

Not sure if that may be the problem?  Any ideas?

---

### Post by Lockheed on 2009-10-04
> **GJCT said:**
> Well, I can record and playback my recording with sound recorder, and it works fine, but, while I am recording, nothing shows up under the "recording" tab of the padevchooser programme. I understand that it should show the levels.

I guess my system is screwed on some deeper level since it is using on-board ES1869 soundcard from 1998 and I cannot record at all (that is, I can but it records silence).

---

### Post by GJCT on 2009-10-04
Does anyone know how to revert to the old version of skype? That worked fine...

---

### Post by Lockheed on 2009-10-04
I eventually got Skype to work (although Recording in other programs still doesn't work).
I removed pulse and installed esound. I don't know if it's being used thought, since all settings point to ALSA.

Anyway, now test call does record my voice. The problem is, it is at low volume (all volume sliders are maxed) and with erratic cracks all over.
If I go to windows, recordings are clear and veyr loud. 

No idea why linux is so backward with voice recording.

---

### Post by pdc124 on 2009-11-01
and upgrading to 9.10 doesnt fix it either 
:(

---

### Post by GJCT on 2009-11-01
But chaining back to the old version of Skype works!

:-)

---

### Post by pdc124 on 2009-11-04
RtApiAlsa: callback thread error (RtApiAlsa: audio write error for device (C-Media CMI8738 (hw:CMI8738,0)): Unknown error 405.) ... closing stream.

 is the current error message 

How do i chain it back ? 

This really is very very frsutrating .

---

