---
title: "Xine DVD playback, major problem"
date: 2006-02-14
forum: General Help
---

### Post by speedsix on 2006-02-14
The dvd plays fine through to the main menu, however on certain dvds when I select play film it throws an error 'The audio device is unavailable. Please verify if another program already use [sic] it.'

The only option I have set is the audio to 'passthrough', works fine if I leave it set to 2.0 but I need it passed through to an external decoder. Mplayer plays fine but i dont want to use this as it has no menu support.

I really need this fixed, many thanks.

---

### Post by super on 2006-02-14
have you tried using a different sound system in xine? alsa, oss and esd all work for me.

---

### Post by speedsix on 2006-02-15
Alsa gives the error, oss no sound and esd is badly synched :( 

I generally use alsa for everything, I have a custom alsa script so I can use the spdif out.


Thanks

---

### Post by nt_bert on 2006-02-15
speedsix,

How are you/did you configure your alsa to get to the SPDIF out ? I have spend a good deal of time over the past 4 weeks dealing with my ALSA and spdif out, I may be able to help if I knew a little more about your setup.

Are you using a .asoundrc ? Would you post it?
What is the sound card that you are using ?
Have you tried downloading xine from source and compiling and installing it?
Which player are you using? (The Xine front end, Totem-Xine, etc) 

Thanks, 
Sean P 



[QUOTE=speedsix]Alsa gives the error, oss no sound and esd is badly synched :( 

I generally use alsa for everything, I have a custom alsa script so I can use the spdif out.


Thanks[/QUOTE]

---

### Post by speedsix on 2006-02-16
Hi there, I have attached my /etc/asound.conf at the bottom of this post.

Soundcard is an onboard nForce2, I am currently using the plain xine-ui but I've just been trying to compile the latest xine from source but not being very successful atall.

Many thanks

```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
     device 2
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

```

---

### Post by nt_bert on 2006-02-16
Here is what I would do, first I would try a very simple asoundrc file. I did mention the bare minimum in the following thread. If you can get that to work, I would then slowly add functionality to the .asoundrc file.

The hint on recompiling XINE is to 1) Install the alsa-headers and 2) use sudo to do a configure, make and make install. For some reason, doing a non-sudo version of the configure and make gave me errors. Did I mention that you can read my trials and tribulations with XINE, ALSA and HDTV at :

[http://www.ubuntuforums.org/showthread.php?t=88203](http://www.ubuntuforums.org/showthread.php?t=88203)

Please do let me know if that helped and if I can be of further help.

Sean P., MCSE.

---

### Post by speedsix on 2006-02-17
Excellent I'll give that a try later, thanks alot.

I really love linux but all these sound servers really give me a headache :cry:

---

### Post by Revolution on 2006-02-17
On the subject of playing DVDs, when I did an Edubuntu install (5.10) I couldnt play DVDs with Totem.
=========================================
totem could not play 'dvd://'
there were no decoders found to handle the stream
=========================================

What magic do I need to perform to get DVDs to play?
Do I need a decrypter?

---

### Post by nt_bert on 2006-02-19
Revolution, please see this thread :
[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

Let me know if I can be of further assistance.

Sean P, MCSE.

---

### Post by speedsix on 2006-02-20
Thanks that worked. I've modifed it to have software mixing with dmix, All I changed is the device from 0,0 to 0,2 for my digital output.

---

### Post by nt_bert on 2006-02-21
Glad I could help.

Sean P, MCSE.

---

