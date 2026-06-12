---
title: "Skype &amp; Audio"
date: 2010-01-04
forum: General Help
---

### Post by Remanifest on 2010-01-04
I'm having a problem with Skype that I'm hoping someone can help with.  I'm on Ubuntu Karmic, and running Skype 2.0.0.72 -- since I couldn't get the latest version to work with my USB microphone.  If I have Skype running, no other programs will produce sound (i.e. Amarok, VLC, flash in the browser, etc.).  If any of those programs are active when I start Skype, Skype will fail to produce sound & won't work properly.

Is there a way I can allow side-by-side usage of Skype and my other audio-producing programs, since all my other programs seem to get along just fine when it comes to sharing audio?

Audio Devices in Skype in case it will help:
Sound In:  USB Device 0x471:0x311 (hw:U0x4710x311,0)
Sound Out:  C-Media CMI8770 (plughw:CMI8770,0)
Ringing:  C-Media CMI8770 (plughw:CMI8770,0)

Again, both my current Skype configuration & sound in general programs works on my system -- they're just not playing well with each other.

---

### Post by pedro_orange on 2010-01-04
I think you need to tell Skype to use ALSA, have you checked that section on [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

You can test it works by running:

> aoss skype

Before making any changes permanent.

---

### Post by Remanifest on 2010-01-04
Thank you for your prompt reply.  I ran "aoss skype" as directed, to no avail.  Here are the results of that command:

```
$ aoss skype 
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.                                                                                       
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi 
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi 
bt_audio_service_open: connect() failed: Connection refused (111)                       
bt_audio_service_open: connect() failed: Connection refused (111)                       
bt_audio_service_open: connect() failed: Connection refused (111)                       
bt_audio_service_open: connect() failed: Connection refused (111)                       
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi 
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi 
bt_audio_service_open: connect() failed: Connection refused (111)                       
bt_audio_service_open: connect() failed: Connection refused (111)                       
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
```

I am running an AMD64 version of Kubuntu -- not sure if that will make a difference or not here.

---

### Post by PAKSHAN on 2010-01-05
Skype is arguably the most popular Web telephony service out there. Using [Skype]("http://www.skype.com/"), you can easily make calls from one PC to another, or from a PC to telephone -- anywhere in the world.

One common complaint about Skype is that the quality of the calls varies widely. If you've used Skype for any length of time, you know what I'm talking about: echoes, sound delays, the sound dropping out, and even calls being dropped. There are a number of simple changes that you can make to both your system settings and the settings of your Skype client software to improve the audio quality of your Skype calls.
============================================
[LIMS Software](http://labface.com/suppliers/LIMS-Software-33)
[affiliate guide](http://www.affiliateleap.com/)

---

### Post by jamesisin on 2010-01-05
Try going through this PulseAudio guide (it includes information on properly configuring Skype for simultaneous playback with other applications):

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

You may want to go through this comprehensive audio/video fixit page:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I do these on all the machines I build now.

---

