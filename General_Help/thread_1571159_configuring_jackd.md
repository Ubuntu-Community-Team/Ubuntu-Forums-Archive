---
title: "configuring jackd ?"
date: 2010-09-09
forum: General Help
---

### Post by jfreak_ on 2010-09-09
So I was installing some updates ( with guido-iodice ppa enabled) and I get this message box asking me to configure jackd. It asks me whether I want to 'enable realtime process priority'. There is a help button on the side which on being clicked gives a pop up saying
'If you want to rin jackd with realtime priorities, the user starting jackd needs realtime permissions. Accept this option to create the file /etc/security/limits.d/audio.conf, granting realtime priority and memlock priviliges to the audio group.
running jackd withrealtime priority minimizes latency but may lead to complete system lockups by requesting all the available physical system memory, which is unacceptable in multi-user environments'

So what is this all about? this is like greek and latin to me. Help.

---

### Post by Vigh on 2010-09-09
jackd is a basic audio-sound system/server for linux, it is particularly useful for audio production and midi i believe, real-time only works on real-time kernel or the real-time ubuntu system, but you can run jackd sound server on a generic kernel it just has slightly more latency when doing professional audio, you can run jackd along side pulseaudio and alsa, but the soundcard will only use either jackd or pa/alsa at one time, just click no for real-time priority and continue with your installation

---

