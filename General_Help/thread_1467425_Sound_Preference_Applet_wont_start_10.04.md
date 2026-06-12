---
title: "Sound Preference Applet wont start 10.04"
date: 2010-04-30
forum: General Help
---

### Post by segisaurus on 2010-04-30
Ubuntu 10.04LTS

Installed Skype and had audio playback issues with pulse audio.  Fixed that with 

> killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

now skype works but the sound is maxed out.  It's like talking to Loud Howard from Dilbert.  I'm using a Logitech USB headset.  It has a volume control button that is not responding.  So I tried opening sound preferences from System>Preferences>sound so I could tell the system to let the headset change the volume.  But I simply get a message stating "Waiting for Sound System to respond" which it never does.  

On board sound.  Mother board is a gigbyte Model MA770-UD3

I never tried to open sound preferences before so I don't know if it was never working or if the skype fix is causing the problem.  Any clues as to whats wrong.

---

### Post by GSF1200S on 2010-04-30
> **segisaurus said:**
> Ubuntu 10.04LTS

Installed Skype and had audio playback issues with pulse audio.  Fixed that with 



now skype works but the sound is maxed out.  It's like talking to Loud Howard from Dilbert.  I'm using a Logitech USB headset.  It has a volume control button that is not responding.  So I tried opening sound preferences from System>Preferences>sound so I could tell the system to let the headset change the volume.  But I simply get a message stating "Waiting for Sound System to respond" which it never does.  

On board sound.  Mother board is a gigbyte Model MA770-UD3

I never tried to open sound preferences before so I don't know if it was never working or if the skype fix is causing the problem.  Any clues as to whats wrong.

Well, I dont know how to get that applet working. Pulseaudio is a mess for many of us (myself included). I can at least suggest running:
```
alsamixer
```
in a terminal so you can at least turn the volume down to usable levels. I dont have pulseaudio either, but XFCE has an alsa panel applet that allows me to control my sound levels. Perhaps you could try to Add Item To Panel and see if it has such an applet? Sorry I cant be more help...

---

### Post by segisaurus on 2010-04-30
The alsa mixer shows a greyed out control for headphone.  I turned the master volume to 0 it was still screaming at me.  But thankyou for the help.  

I noticed while trying to search the forums that pulse ausio causes a lot of pproblems for people.  Why is it the default application?

---

### Post by GSF1200S on 2010-04-30
> **segisaurus said:**
> The alsa mixer shows a greyed out control for headphone.  I turned the master volume to 0 it was still screaming at me.  But thankyou for the help.  

I noticed while trying to search the forums that pulse ausio causes a lot of pproblems for people.  Why is it the default application?

What about PCM? That one will usually always bring the volume down. By the way, if you cannot adjust the volume, try hitting 'm' to invoke (or un-invoke) mute. This will not work on PCM. Does it have front or anything else? Maybe you could post a screenshot of alsamixer so I can help you.. Its strange though.. it works for me and I dont have pulseaudio (i dont have esound either).

---

