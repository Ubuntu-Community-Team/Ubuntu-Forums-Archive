---
title: "PulseAudio - changing channel map. Output comes out of the wrong speaker in 5.1!"
date: 2011-12-25
forum: General Help
---

### Post by g0l3m on 2011-12-25
Hi all (and Merry Xmas),

I've been struggling with this for a day now...Read up lots of posts, tried lots of solutions, no luck! My problem (in theory) is very simple. In my 5.1 configuration the wrong sound comes out of the wrong speaker. So, I just need to change my channel map (correct me if I'm wrong on this). Here's what list-sinks in pacmd shows:

sample spec: s16le 6ch 44100Hz
channel map: front-left,front-right,rear-left,rear-right,front-center,lfe
Surround 5.1

Here's the output from speaker-test -c6 -l1 -twav:

speaker-test 1.0.24.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 349525
Period size range from 10 to 116509
Using max buffer size 349524
Periods = 4
was set period_size = 87381
was set buffer_size = 349524
 0 - Front Left
 4 - Centre
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 9.278501

Trouble is only 2 of these are correct, the front-left and front-right. The others are in weird order, e.g. center comes out from rear-left, rear-left comes out of the subwoofer, etc.

Here's what I've tried so far (having searched A LOT):

In /etc/pulse/daemon.pa changed sample channels to 6 (and also the default channel map) - no joy.

In /etc/pulse/daemon.conf changed system.pa and default.pa to not load the autodetect modules but instead use module-remap-sink as per [http://confignewton.com/?p=211](http://confignewton.com/?p=211) - no joy.

In /usr/share/pulseaudio/alsa-mixer/profile-sets/ changed the channel map in default.conf for the 5.1 configuration - no joy.

This last solution I was hoping would do the trick but when I list-sinks in pacmd the order seems to be the same all the time.
Essentially, all I need is instead of:

channel map: front-left,front-right,rear-left,rear-right,front-center,lfe

to have this:

channel map: front-left,front-right,lfe,front-center,rear-left,rear-right

I'm hoping I'm missing something really obvious and the solution is pretty straight forward. Please help if you can!
If you require any addition info please do ask. This is on a brand new 11.10 installation with:

alsa.card_name = "Intel ICH5"
alsa.long_card_name = "Intel ICH5 with AD1985 at irq 17"
alsa.driver_name = "snd_intel8x0"

3 jacks at the back of the card to connect to speakers.

cheers,
g.

---

### Post by g0l3m on 2011-12-28
bump! - can someone please help with this...still an issue...still no idea how to do it. all I want it to change some of the output from where it's going to somewhere else...e.g. send front-center to real-left, etc.

---

### Post by g0l3m on 2012-01-03
bump!

Pretty please? I'm assuming I'm doing something wrong and it's not that hard to actually change the speaker mapping.

All I want is for example the front-center to be the real-left!

Please, can anyone help?

g.

---

### Post by rjf1 on 2012-01-04
You would probably stand a better chance of getting help in the Multimedia & Video forum.

---

