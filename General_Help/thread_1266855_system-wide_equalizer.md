---
title: "system-wide equalizer"
date: 2009-09-15
forum: General Help
---

### Post by ithinkitschad on 2009-09-15
Hey, I'm tryin to find a system-wide equalizer. If you dont get what I'm saying, I want an equalizer for my entire system, so I turn the bass down, then the bass is lower on every program. Does anyone know a good program for this. I'm running jaunty.

Thanks,
       Cchhaadd

---

### Post by ithinkitschad on 2009-09-15
bump?

---

### Post by P4man on 2009-09-15
20 minute bumps is quite rude TBH.
Anyway, a 2s google gives me this:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by ithinkitschad on 2009-09-15
> **P4man said:**
> 20 minute bumps is quite rude TBH.
Anyway, a 2s google gives me this:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I bumped it becuase I don't seem to see any of my posts come up on "New Posts" so it seems odd. I'd also like not to install PulseAudio. I'd like an equalizer that can run with alsa.

and you were the first "view" in about a half an hour

---

### Post by ithinkitschad on 2009-09-15
It seems unnecessary to switch to pulse just to have an equalizer

---

### Post by danwood76 on 2009-09-15
> **ithinkitschad said:**
> It seems unnecessary to switch to pulse just to have an equalizer

The equaliser is provided by ALSA not pulse. (well done for reading the thread)

Pulseaudio is the default in Ubuntu and works well in the latest Karmic release (Jaunty was a bit rough in places but generally good and intrepid had great pulse support)

---

### Post by ithinkitschad on 2009-09-15
ooo

---

### Post by P4man on 2009-09-15
people like me regularly browse through several pages of threads looking for stuff that we might help out with and/or click the "unanswered" link to find posts that haven't gotten a reply in 12 hours. Bumping, especially after 20 minutes actually ensures we'd miss it.

Anyway, i don't think its possible with alsa. Even with pulse its a bit of a hack.

---

### Post by ithinkitschad on 2009-09-15
> **danwood76 said:**
> The equaliser is provided by ALSA not pulse. (well done for reading the thread)

Pulseaudio is the default in Ubuntu and works well in the latest Karmic release (Jaunty was a bit rough in places but generally good and intrepid had great pulse support)

"The equaliser is provided by ALSA not pulse. (well done for reading the thread)"

You lost me, what do you mean?

---

### Post by ithinkitschad on 2009-09-15
> **P4man said:**
> people like me regularly browse through several pages of threads looking for stuff that we might help out with and/or click the "unanswered" link to find posts that haven't gotten a reply in 12 hours. Bumping, especially after 20 minutes actually ensures we'd miss it.

Anyway, i don't think its possible with alsa. Even with pulse its a bit of a hack.

Oh, I apologize that makes sense, your a good person then you help people like me out. Sorry for being so cynical

---

### Post by danwood76 on 2009-09-15
ALSA is the audio driver not pulseaudio, ALSA will control your soundcard and pulse acts like an audio server on top.
Its possible to implement the equaliser from that thread in ALSA as that is all the configuration does and pulse uses the underlying ALSA equaliser.

Why do you not use Pulse?

---

### Post by ithinkitschad on 2009-09-15
> **danwood76 said:**
> ALSA is the audio driver not pulseaudio, ALSA will control your soundcard and pulse acts like an audio server on top.
Its possible to implement the equaliser from that thread in ALSA as that is all the configuration does and pulse uses the underlying ALSA equaliser.

Why do you not use Pulse?

That makes sense. The reason I dont want to use pulse is because the last time I used it a long time ago i ended up having some problem where I couldnt get my sound to work. I guess I should give it a second chance, that was when i was first using linux.

---

