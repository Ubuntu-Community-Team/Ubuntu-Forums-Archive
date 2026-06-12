---
title: "How do I make hdmi audio output work?"
date: 2010-11-12
forum: General Help
---

### Post by barfo666 on 2010-11-12
Greetings,

I'm running Ubuntu 10.04 in a Dell XPS M1330 laptop with Intel gma X3100 integrated graphics.

I occasionally use it for watching movies in an LCD TV, however when I connect it I can get it to output video fine, but audio is a no go, when I select hdmi audio in the sound options I get no sound.

Can anybody help please? this is the only thing I need to solve before getting rid of Windows.

---

### Post by barfo666 on 2010-11-12
bump

---

### Post by dcstar on 2010-11-12
> **barfo666 said:**
> Greetings,

I'm running Ubuntu 10.04 in a Dell XPS M1330 laptop with Intel gma X3100 integrated graphics.

I occasionally use it for watching movies in an LCD TV, however when I connect it I can get it to output video fine, but audio is a no go, when I select hdmi audio in the sound options I get no sound.

Can anybody help please? this is the only thing I need to solve before getting rid of Windows.

Do you HDMI Output options enabled in **System-Preferences-Sound** & **Applications-Sound & Video-PulseAudio Volume Control**?

---

### Post by barfo666 on 2010-11-12
> **dcstar said:**
> Do you HDMI Output options enabled in **System-Preferences-Sound** & **Applications-Sound & Video-PulseAudio Volume Control**?

Thank you for replying.

Yes, if I have the default setting (Analog Stereo Duplex) while playing an mp3 it sounds alright, when I switch to Digital Stereo (HDMI) Out it goes silent. Though I can see the equalizer bar moving, don't know if that means anything.

---

### Post by barfo666 on 2010-11-13
Any more ideas? :)

---

### Post by axept on 2010-11-13
When you listening to music/video go to terminal.

run alsamixer
Go to the right and find S/PDIF, try to mute/unmute (press M) them. Maybe one must be unmuted and one muted, just try. When you get sound, exit alsamixer (Esc) and run:

sudo alsactl store

---

### Post by barfo666 on 2010-11-14
> **axept said:**
> When you listening to music/video go to terminal.

run alsamixer
Go to the right and find S/PDIF, try to mute/unmute (press M) them. Maybe one must be unmuted and one muted, just try. When you get sound, exit alsamixer (Esc) and run:

sudo alsactl store
I tried all the combinations of muting unmiting and I never got sound out of the tv :(

---

### Post by ivarn on 2010-11-14
Well, if you have an ok internet connection and a game console (xbox360 or ps3) you can watch the videos over a media server.

---

### Post by elcamilo on 2011-01-09
same Dell XPS M1330 laptop with Intel gma X3100 integrated graphics for me, and with Ubuntu 10.10 I have no sound on hdmi tv peripherals.

so we can't make it works, right?

---

### Post by tn812 on 2011-02-07
Seems like no real solution for this yet.

I'm having the same problem, no hdmi audio out.  Anyone has a solution or suggestion?  I'm using ubuntu 10.10.  Will 10.04 be any better?

---

### Post by Docaltmed on 2011-02-14
I've been going down this road, too. I've tried all of the alsamixer tricks, I've updated ALSA to the newest version, I've created an asound.conf file and populated it as instructed....nothing.

The really weird thing is that the sound had been working fine, until one day...it just stopped.

It is not a receiver/cable problem, in that I can plug in my laptop -- Ubuntu 10.04 as well -- and immediately get sound.

It just doesn't make sense.

---

### Post by madhusker on 2013-02-24
Appears to be impossible as all I can find are dead threads on the internet.  :mad:

---

