---
title: "GoogleVoice problem. I cannot hear who I call"
date: 2011-03-23
forum: General Help
---

### Post by windeguy on 2011-03-23
I had no problems using Googlevoice within gmail on Firefox until a recent normal update caused a problem.  The update stopped my microphone from working anywhere in Ubuntu. 

Deleting pulse audio got my microphone to work again in Ubuntu. I can also use SKYPE again without a problem. 

But now I cannot hear the party I am calling using GoogleVoice. I hear the phone ringing sound, but when the party I called picks up I cannot hear them.  I have deleted and re-installed the google-talk plugin necessary for googlevoice, but that did not help. I have no problem hearing audio from other sources like Youtube, Ardour, SKYPE, etc. 

Any suggestions?

---

### Post by tgalati4 on 2011-03-23
Do you have pavucontrol and pavumeter installed?

sudo apt-get install pavucontrol pavumeter
pavumeter &
pavucontrol &

Fiddle with the settings to see if your microphone level and boost is set properly.

---

### Post by windeguy on 2011-03-23
> **tgalati4 said:**
> Do you have pavucontrol and pavumeter installed?

sudo apt-get install pavucontrol pavumeter
pavumeter &
pavucontrol &

Fiddle with the settings to see if your microphone level and boost is set properly.

Thank you for the response, but I was trying to avoid re-installing Pulse Audio.  pavucontrol and pavumeter are parts of pulse audio. The microphone is working without pulse audio. It is the speakers that are not working when I rung GoogleVoice. I cannot hear the party that I am calling. That is a problem with the audio path to the speakers (not the microphone).

As I mentioned.  I had un-istalled Pulse Audio previously and I had no problem using GoogleVoice until after a normal recommended upgrade of 10.04LTS when something got broken. Any other suggestions?

---

### Post by tgalati4 on 2011-03-23
Did you check your audio settings in gmail, general settings, chat, verify audio?

There is a selection bar to choose "default" audio or specific hardware.  Have you tried changing those settings?

---

### Post by windeguy on 2011-03-23
> **tgalati4 said:**
> Did you check your audio settings in gmail, general settings, chat, verify audio?

There is a selection bar to choose "default" audio or specific hardware.  Have you tried changing those settings?

Yes I did that and tried the different settings to hear playback. Nothing made a difference. I see this response in the call window when I hang up: 

 Sorry! The phone call with (800) 555-1212 failed because of a network problem at 4:23 PM. Please try again.
 Thank you!
 (Error ID: 4ac9624807f3ff4a)

It doesn't matter what number in the US I call. It fails.

---

